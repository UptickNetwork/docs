# Mobile(WalletConnect)

[WalletConnect](https://walletconnect.org/) is an open source protocol for connecting dApps to mobile wallets with QR code scanning or deep linking, basically it's a websocket JSON-RPC channel.

With WalletConnect, your users can use Mobile apps as a signer while using other web, desktop, or mobile apps. Read the [WalletConnect mobile linking documentation](https://docs.walletconnect.org/mobile-linking) for more information.

There are two common ways to integrate: Standalone Client and Web3Model (Web3 Provider)

## Standalone Client

Metamask or other mobile wallet app  with aditional JSON-RPC methods to support multi-chain **dApps**. Currently, you can get all accounts and sign transactions for Uptick network implements `signJSON` method in wallet core.

### Installation

```bash
npm install --save @walletconnect/client @walletconnect/qrcode-modal
```

### Initiate Connection

Before you can sign transactions, you have to initiate a connection to a WalletConnect bridge server, and handle all possible states:

```javascript
import WalletConnect from "@walletconnect/client";
import QRCodeModal from "@walletconnect/qrcode-modal";

// Create a connector
const connector = new WalletConnect({
  bridge: "https://bridge.walletconnect.org", // Required
  qrcodeModal: QRCodeModal,
});

// Check if connection is already established
if (!connector.connected) {
  // create new session
  connector.createSession();
}

// Subscribe to connection events
connector.on("connect", (error, payload) => {
  if (error) {
    throw error;
  }

  // Get provided accounts and chainId
  const { accounts, chainId } = payload.params[0];
});

connector.on("session_update", (error, payload) => {
  if (error) {
    throw error;
  }

  // Get updated accounts and chainId
  const { accounts, chainId } = payload.params[0];
});

connector.on("disconnect", (error, payload) => {
  if (error) {
    throw error;
  }

  // Delete connector
});
```

Code snippet above is copied from[ https://docs.walletconnect.org/quick-start/dapps/client#initiate-connection](https://docs.walletconnect.org/quick-start/dapps/client#initiate-connection), please check out the original link for standard methods.

## Web3Modal

[Web3Modal](https://github.com/Web3Modal/web3modal) is an easy-to-use library to help developers add support for multiple providers (including WalletConnect) in their apps with a simple customizable configuration.

### Installation

```bash
npm install --save web3modal web3 @walletconnect/web3-provider
```

### Customize chain id

Sample code for configuring WalletConnect with Binance Smart Chain

```js
import Web3 from "web3";
import WalletConnectProvider from "@walletconnect/web3-provider";
import Web3Modal from "web3modal";

// set chain id and rpc mapping in provider options
const providerOptions = {
  walletconnect: {
    package: WalletConnectProvider,
    options: {
      rpc: {
        117: "https://json-rpc.uptick.network",
      },
      chainId: 117,
    },
  },
};

const web3Modal = new Web3Modal({
  network: "mainnet", // optional
  cacheProvider: true, // optional
  providerOptions, // required
});

const provider = await web3Modal.connect();
await web3Modal.toggleModal();

// regular web3 provider methods
const newWeb3 = new Web3(provider);
const accounts = await newWeb3.eth.getAccounts();

console.log(accounts);
```

```
// subscribeToEvents
function subscribeToEvents() {
    const { connector } = appState;

    if (!connector) {
        return;
    }

    connector.on("session_update", async (error, payload) => {
        if (error) {
            throw error;
        }

        const { chainId, accounts } = payload.params[0];
           const address = accounts[0];
    appState.chainId = chainId;
    appState.accounts = accounts;
    appState.address = address;

    await getAccountAssets();

    events.$emit("session_update", appState);
    });

    connector.on("connect", (error, payload) => {

        if (error) {
            throw error;
        }

        const { chainId, accounts } = payload.params[0];
    const address = accounts[0];

    appState.connected = true;
    appState.chainId = chainId;
    appState.accounts = accounts;
    appState.address = address;
    await getAccountAssets();

    events.$emit("connect", appState);
    });

    connector.on("disconnect", (error, payload) => {

        if (error) {
            throw error;
        }

        window.eventBus.$emit("disconnect",appState);
    });

}
```
