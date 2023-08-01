# Template721

Template ERC721 NFT template

```

// load Address
export function setContractAddress(address, platformAddress) {
    if(address) {
        contractAddress = address;
    }
    if(platformAddress) {
        contractAddressPlatform = platformAddress;
    }
}


// transfer Token
export async function transferFrom(toAddress, tokenId) {
    const account = await base.getAccounts();
    const fromAddress = await account.getAddress();

    let contract
    if (!contract) {
        contract = await connect(contractAddress, abi, account);
    }
let hasWalletConnect = isWalletConnect();
	if(!hasWalletConnect){
		let gasSetting = await base.getGasPriceAndGasLimit();
		console.log("gasSetting", gasSetting);
		let result = await contract.transferFrom(
		    fromAddress, toAddress, tokenId,
		    { gasPrice: gasSetting.gasPrice, gasLimit: gasSetting.gasLimit }
		);
		return result;
	}else{
		  let data= contract.methods.transferFrom(fromAddress, toAddress, tokenId).encodeABI()
		let result = await wallectConnectSendTransaction(fromAddress,contractAddress,data,"0");
		return result;
		 
	}
	
	

}



// mint
export async function mintNft( toAddress,tokenId,baseurl,mintByCreatorFee) {
     const account = await base.getAccounts();
    const fromAddress = await account.getAddress();

    let contract
    if (!contract) {
        contract = await connect(contractAddress, abi, account);
    }

    

let hasWalletConnect = isWalletConnect();
	if(!hasWalletConnect){
		let gasSetting = await base.getGasPriceAndGasLimit();
		console.log("gasSetting", gasSetting);
		let result = await contract.mintByCreatorFee(
		    toAddress, tokenId, baseurl,mintByCreatorFee,
		    { gasPrice: gasSetting.gasPrice, gasLimit: gasSetting.gasLimit }
		);
		return result;
	}else{
		  let data= contract.methods.mintByCreatorFee(toAddress, tokenId, baseurl,mintByCreatorFee).encodeABI()
		  debugger
		let result = await wallectConnectSendTransaction(fromAddress,contractAddress,data,"0");
		return result;
		 
	}
	
}

export async function isApprovedForAll() {
    debugger
    const account = await base.getAccounts();
    const fromAddress = await account.getAddress();

    let contract
    if (!contract) {
        contract = await connectCheck(contractAddress, abi, account);
    }
    let result = await contract.isApprovedForAll(
        fromAddress, contractAddressPlatform
    );
    console.log("isApprovedForAll", result);
    return result;
}

export async function setApprovalForAll() {
    const account = await base.getAccounts();
    const fromAddress = await account.getAddress();

    let contract
    if (!contract) {
        contract = await connect(contractAddress, abi, account);
    }
    	
let hasWalletConnect = isWalletConnect();
	if(!hasWalletConnect){
		let result = await contract.setApprovalForAll(
		    contractAddressPlatform, true
		);
		console.log("setApprovalForAll", result);
		return result;
	}else{
        let gasSetting = await base.getGasPriceAndGasLimit();
		let data= contract.methods.setApprovalForAll(contractAddressPlatform, true).encodeABI()
		let result = await wallectConnectSendTransaction(fromAddress,contractAddress,data,"0", { gasPrice: gasSetting.gasPrice, gasLimit: gasSetting.gasLimit });
		return result;
		 
	}
	
}

```
