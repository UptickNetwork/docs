# Communicate with  blockchains（JS）

Wallets use JSON-RPC to communicate with  blockchains.

## Accessing the Injected Provider

The Injected Provider is a global object that implements all the methods of the [EIP-1193](https://eips.ethereum.org/EIPS/eip-1193) specification and is available as `window.ethereum`.

We already mentioned in the previous section that each wallet injects its provider, so the question that naturally arises is: What is the value of `window.ethereum` when multiple injected providers exist, ie users have multiple wallets installed?

There are times when users might have multiple wallets installed in their browsers which can cause one wallet Injected Provider to override another. [EIP-5749](https://eips.ethereum.org/EIPS/eip-5749) tries to fix that, but until it gets approved and adopted, there is no standardized way of solving this issue. Some wallets, such as Trust Wallet, define `window.ethereum.providers` array to save other Injected Providers from overriding. The value of `window.ethereum` when multiple wallets are installed, is non-deterministic, but usually, the last Injected Provider wins. Most wallets define their flag in their respective providers to distinguish them from other wallet providers.Developers can read the presence of those flags to determine which wallet the corresponding provider refers to.&#x20;

To sum up, there are three places where we can check the existence of the TW injected provider: in `window.ethereum` by checking&#x20;

Let's implement a function `getWalletFromWindow` that will allow us to retrieve the TW provider.

```jsx
function getWalletFromWindow() {
  	var web3;
	if (window.ethereum) {
		// Modern dapp browsers
		web3 = new Web3(window.ethereum);
		try {
			await window.ethereum.enable();
            await window.ethereum.eth_requestAccounts();
          
		} catch (error) {
			console.log('denied');
		}
	} else {
		this.$Message.error('metamask Unconnected！');
	}
}
 
```

`getWalletFromWindow` will return either the  Waller Injected Provider or `null` if it cannot be found. We can assume that if the function returns `null`, TW is not installed in the user's browser. But wait, there is a catch!

An [issue affects web extensions that utilize manifest V3](https://groups.google.com/a/chromium.org/g/chromium-extensions/c/ib-hi7hPdW8/m/34mFf8rrGQAJ?pli=1) and causes the injected provider to be initialized after the website loads. In that case, we must wait for the `wallet#initialize` event.

```jsx
async function listenForWalletInitialized(
 
) {
    let web3Provider = new ethers.providers.Web3Provider(window.ethereum);
  let signer = await web3Provider.getSigner();
    return signer;
}
```

`listenForWalletInitialized` registers a listener for the `wallet#initialization` event that resolves to the  Wallet Injected Provider or `null` if it cannot be retrieved after a specific timeout. The default timeout value is set to 2 seconds, which is more than enough.

Connecting to  Wallet means accessing the user's selected account. This is different than what you may be used to when developing authenticating logic in web2 apps. Connection to web3 wallets is stateless and serves more like a "pairing" mechanism. There is no concept of "logging/authenticating into wallet". Once you request access to the wallet, this access is kept until the users choose to disconnect/unpair the wallet from your website.

Requesting access to a user's account can be achieved through the `eth_requestAccounts` method.

```jsx
window.ethereum.eth_requestAccounts();
```

If a connection were established beforehand, the returning result would be an array with only one element: the selected account.

Otherwise, a notification will appear to users if a previous connection was not established, prompting them to initialize a new connection. If the user decides to reject this request, the promise will be rejected with a status code of `4001` . You can read more about various error status codes [here](https://eips.ethereum.org/EIPS/eip-1193#provider-errors).

### Get selected account

You can access the selected account for a connected wallet at any point in time using the `eth_accounts` method. Like `eth_requestAccounts`, the returning value will be an array with only one element: the selected account. The distinction is that `eth_accounts` assumes a connection is already established. If this is not the case, the returned value will be an empty array. No connect notification will be sent to the user.

```jsx
const accounts = web3.eth.requestAccounts();
```

### Listening for accounts change & disconnect events

Users are allowed to change their connected accounts from within their wallets, as well as to disconnect entirely. You will have to update your website state to accommodate the new account state change when this happens. This can be achieved by listening to the `accountsChanged` event. The callback offers one parameter `accounts` which is an array that will contain one element, the new selected account, or zero elements when users disconnect their wallets. Most times you have to combine the accounts changed and disconnect logic into the same event listener.

```jsx
window.ethereum.on('accountsChanged', handleAccountsChanged);
```

### Listening for chain id change events

Changing the connected chain id is also another everyday use case for users. For instance, many decentralized exchanges support multiple networks and offer that functionality to their users.

As a developer, you can listen to `chainChanged` events. The callback will contain the new chain id in either hexadecimal or decimal format.

```jsx
window.ethereum.on('chainChanged', handlechainChanged);
```

> **Tip**: You can use `parseInt` without specifying the radix to convert it to number type.

Each blockchain has its chain id. You can use a website like [https://chainlist.org/](https://chainlist.org/) to find out which chain id pairs to what network.

### Request chain id change

You can also request a chain id change yourself. Most dApps are published to specific blockchains, so you want to ensure that users are connected to the correct chain. This can be achieved using `wallet_switchEthereumChain` method and passing the hexadecimal value of the desired chain.

```jsx
try {
  await injectedProvider.request({
    method: "wallet_switchEthereumChain",
    params: [{ chainId: "0x75" }], // Ensure the selected network is Etheruem
  });
} catch (e) {
  if (e.code === 4001) {
    setError("User rejected switching chains.");
  }
}
```

A notification will appear if users are not connected to the desired network, prompting them to change their network. Users who reject this request will trigger an error with `4001` as the status code. If the desired network is selected, this request will resolve without any additional action required by the user.

### Get selected chain id

You can access the selected chain at any point in time using the `eth_chainId` method. You don't need an active connection to execute this method successfully.

```jsx
const chainId = await injectedProvider.request({ method: "eth_chainId" });
```

## Interacting with smart contracts

Pairing a website with the Trust Wallet browser extension is only half the story. We often request access to the wallet to interact with a smart contract (dApp). We will dedicate the following examples to explain how to set up your environment for production use and discuss some common best practices.

### Introducing Ethers.js

Using the available methods of the Injected Provider will work for small applications. Still, as you scale into more complex projects requiring constant communication with the blockchain or more advanced functionalities like message signing and contract interaction, the best solution is to integrate a web3 library that will provide a higher level of abstraction. Meet [ethers.js](https://www.npmjs.com/package/ethers), a robust, popular, production-ready web3 library with millions of monthly downloads that will help you achieve your production requirements. Let's see how easy it is to get started.

First, you will have to install it into your project

```jsx
npm i ethers@5
```

Ethers library exposes the core module as a named export.

```jsx
import { ethers } from "ethers";
```

As we said, ethers provide an abstraction layer to common functionalities. To initialize it, you have to pass the Injected Provider, and you are ready to use it!

```jsx
const ethersProvider = new ethers.providers.Web3Provider(injectedProvider);
```

You can learn more about ethers from their [official documentation](https://docs.ethers.org/v5/).

### Retrieving the account balance

To retrieve the account balance, you can call `getBalance`. The method accepts the public address in string format and returns a promise which will resolve into a [BigNumber](https://docs.ethers.org/v5/api/utils/bignumber/) object.

```jsx
const web3Obj = new Web3(uptickUrl);
const account = "0x...";
let accountBalance = web3Obj.eth.getBalance(account);
```

You probably want to further process the return value into a primitive type like string or number. The BigNumber library offers many convenient methods like `toString` or `toNumber` .

### Calling a non-payable smart contract function

To interact with a smart contract, you will need the following two things:

* The deployed address
* The smart contract ABI

DApp developers can verify their smart contracts and make their source code publicly available. We can search the token name and get all the information relating to that address, like its deployed address, the total transaction activity, etc.

For TWT the deployed address is `0x4B0F1812e5Df2A09796481Ff14017e6005508003`, time to get the ABI. The [Application Binary Interface (ABI)](https://docs.soliditylang.org/en/latest/abi-spec.html) of a smart contract **gives a contract the ability to communicate and interact with external applications and other smart contracts.** This will allow ethers to construct the request object and call the required methods successfully. To access the ABI through [https://evm-explorer.uptick.network/](https://evm-explorer.uptick.network/) go to "Contract" → "Code" and scroll down until the "Contract ABI" section". Then copy-paste it into a JSON file. For this example, we will create a file `twtABI.json` and paste the ABI there.



To get the balance of an account, we use the `balanceOf`function. The function requires one parameter: the address to retrieve its TWT token balance.

Now that we've gather all pieces of the puzzle, it's time to write some code. First, we import the ethers library and the contract ABI.

```jsx
import { ethers } from "ethers";
import twtABI from "./twtABI.json";
```

Then we declare a constant variable `TWT_ADDRESS` for the smart contract address,

```jsx
const TWT_ADDRESS = "0x4B0F1812e5Df2A09796481Ff14017e6005508003";
```

and create a variable called `ethersProvider`.

```jsx
const account = "0x...";
const ethersProvider = new ethers.providers.Web3Provider(injectedProvider);
```

`account` holds the public address of the desired wallet we want to check the TWT balance. The last step of this set up is to create a [`Contract`](https://docs.ethers.org/v5/api/contract/contract/) instance. This will allow us make requests to the blockchain for the specified smart contract.

```jsx
const contract = new ethers.Contract(TWT_ADDRESS, twtABI, ethersProvider);
```

The first parameter is the contract address. The second is the contract's interface, ie ABI, and the third is the ethers provider instance.

We can now access any defined function by calling it directly from the `contract` instance.

```jsx
const rawBalance = await contract.balanceOf(account);
```

Note that `balanceOf` will return the raw balance value. If we want to convert it to a decimal representation, we need to call `ethers.utils.formatUnits` and pass the `decimals` value as the second parameter.

```jsx
const decimals = await contract.decimals();
const rawBalance = await contract.balanceOf(account);

const accountBalance = ethers.utils.formatUnits(rawBalance, decimals);
```

Here is a complete example in React to retrieve the current TWT balance for the connected account.

```jsx
import {
    connect,
	connectCheck,
	wallectConnectSendTransaction,
	isWalletConnect
} from "./common";

import {
    abi
} from "../artifact/IERC20.json";

const base = require('./base');

//xxl todo get from .evn
let contractAddress,contractAddressPlatform;


export function setContractAddress(token20Address,platformAddress) {

    if(token20Address) {
        contractAddress = token20Address;
    }
    if(platformAddress) {
        contractAddressPlatform = platformAddress;
    }
    
}


export async function getTokenBalance(owner) {
    debugger
    const account = await base.getAccounts();

    let contract
    if (!contract) {
        contract = await connectCheck(contractAddress, abi, account);
    }

    let result = await contract.balanceOf(
        owner
    );
    let balance = result._hex.slice(2)
    result=hex2int(balance)/1000000
    return result;


}

export async function isApprovedForAll() {
    const account = await base.getAccounts();
    const fromAddress = await account.getAddress();

    let contract
    if (!contract) {
        contract = await connectCheck(contractAddress, abi, account);
    }
    let result = await contract.allowance(
        fromAddress, contractAddressPlatform
    );
    console.log("isApprovedForAll", result);
    return result;
}

export async function setApprovalForAll(price) {
    const account = await base.getAccounts();
    const fromAddress = await account.getAddress();

    let contract
    if (!contract) {
        contract = await connect(contractAddress, abi, account);
    }
    
	
	
	let hasWalletConnect = isWalletConnect();
	if(!hasWalletConnect){
		let gasSetting = await base.getGasPriceAndGasLimit();
    let result = await contract.approve(
        contractAddressPlatform,price,
        { gasPrice: gasSetting.gasPrice, gasLimit: gasSetting.gasLimit }
    );
	
	console.log("setApprovalForAll", result);
	return result;
	}else{
		  let data= contract.methods.approve(  contractAddressPlatform,price).encodeABI()
		let result = await wallectConnectSendTransaction(fromAddress,contractAddress,data,"0");
		return result;
		 
	}
	
}
function hex2int(hex) {
    var len = hex.length, a = new Array(len), code;
    for (var i = 0; i < len; i++) {
        code = hex.charCodeAt(i);
        if (48<=code && code < 58) {
            code -= 48;
        } else {
            code = (code & 0xdf) - 65 + 10;
        }
        a[i] = code;
    }
     
    return a.reduce(function(acc, c) {
        acc = 16 * acc + c;
        return acc;
    }, 0);
}




```

### Calling a payable smart contract function

Payable functions require you to pay a certain amount in native currency to execute it. For instance, when you buy an NFT on [OpenSea](https://opensea.io/) you must pay a certain amount of native tokens to complete the transaction (value of the NFT + network fees).

For this example, we will assume a smart contract that offers a `buy` payable function. This smart contract will allow you to buy NFTs from a predefined list for 0.3 Ethers each. To successfully call `buy`, you will need to reference the NFT id.

Calling a payable function with ethers is more or less the same as we would do with any non-payable function. The only difference is that we have to pass an object as last argument that defines a property `value`. We can use `ethers.utils.parseEthers` to convert the string representation to `BigNumber` instance.

```jsx
await contract.buy(NFT_ID, {
  value: ethers.utils.parseEther("0.3"),
});
```

Executing this statement will create a confirmation prompt in user's wallet extension to approve (or reject) the transaction.

