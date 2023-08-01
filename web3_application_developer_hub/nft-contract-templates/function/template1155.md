# Template1155

Template ERC1155 NFT template

```

export function setContractAddress(address, platformAddress) {

    if(address) {
        contractAddress = address;
    }
    if(platformAddress) {
        contractAddressPlatform = platformAddress;
    }
}


// 转送
export async function safeTransferFrom(toAddress, tokenId, countValue) {
    const account = await base.getAccounts();
    const fromAddress = await account.getAddress();

    let contract
    if (!contract) {
        contract = await connect(contractAddress, abi, account);
    }

  
	
	let hasWalletConnect = isWalletConnect();
	if(!hasWalletConnect){
		let gasSetting = await base.getGasPriceAndGasLimit();
		
		let result = await contract.safeTransferFrom(
		    fromAddress, toAddress, tokenId, countValue,utils.toUtf8Bytes(''),
		    { gasPrice: gasSetting.gasPrice, gasLimit: gasSetting.gasLimit }
		);
		return result;
	}else{
		  let data= contract.methods.safeTransferFrom( fromAddress, toAddress, tokenId, countValue,utils.toUtf8Bytes('')).encodeABI()
		let result = await wallectConnectSendTransaction(fromAddress,contractAddress,data,"0");
		return result;
		 
	}
	
	
}

export async function mintNft( toAddress,tokenId,baseurl,royaltyPercentage,amountValue) {
     const account = await base.getAccounts();
    const fromAddress = await account.getAddress();

    let contract
    if (!contract) {
        contract = await connect(contractAddress, abi, account);
    }
	console.log("utils.toUtf8Bytes(baseurl)",utils.toUtf8Bytes(baseurl),baseurl)
	let hasWalletConnect = isWalletConnect();
	if(!hasWalletConnect){
		let gasSetting = await base.getGasPriceAndGasLimit();
		console.log("gasSetting 1155", gasSetting);
		let result = await contract.mintByCreatorFee(
		    toAddress, tokenId, amountValue, utils.toUtf8Bytes('') ,royaltyPercentage,
		    { gasPrice: gasSetting.gasPrice, gasLimit: gasSetting.gasLimit }
		);
		return result;
		
	}else{
		  let data= contract.methods.mintByCreatorFee(toAddress, tokenId, amountValue, utils.toUtf8Bytes('') ,royaltyPercentage).encodeABI();
		  		  console.log("zxx===="+data);
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
    const address = await account.getAddress();

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
		  let data= contract.methods.setApprovalForAll( contractAddressPlatform, true).encodeABI()
		let result = await wallectConnectSendTransaction(address,contractAddress,data,"0");
		return result;
		 
	}
	
	
}

```
