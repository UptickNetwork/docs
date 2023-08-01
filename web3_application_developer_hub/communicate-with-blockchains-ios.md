# Communicate with  blockchains（IOS）



Creating a Wallet:

1. Install web3.swift using CocoaPods or other methods.
2. Import the Web3Swift library in your iOS project.
3. Use the following code to generate a new Ethereum wallet:

```swift
let wallet = try! EthereumKeystoreV3(password: "your_password")
let keystore = try! JSONEncoder().encode(wallet!.keystoreParams)
let jsonString = String(data: keystore, encoding: .utf8)

// Store the jsonString securely, such as in Keychain or User Defaults
```

Sending a Transaction:

1. Import the Web3 class from the Web3Swift library.
2. Connect to the Ethereum network using Infura or any other Ethereum node.
3. Use the following code to send a transaction:

```swift
let web3 = Web3(rpcURL: URL(string: "https://mainnet.infura.io/v3/YOUR_INFURA_PROJECT_ID")!)
let keystore = try! JSONDecoder().decode(EthereumKeystoreV3.self, from: jsonString.data(using: .utf8)!)

let wallet = try! EthereumKeystoreV3Wallet(keystore: keystore)
let password = "your_password"
try! wallet?.regenerate(oldPassword: password, newPassword: password)

let fromAddress = wallet!.address
let toAddress = "0xabcdef1234567890"
let value = BigUInt("1000000000000000000")  // 1 Ether
let gasPrice = BigUInt("20000000000")
let gasLimit = BigUInt("21000")

let transaction = EthereumTransaction(
    from: EthereumAddress(fromAddress)!,
    to: EthereumAddress(toAddress)!,
    value: value!,
    gasPrice: gasPrice,
    gasLimit: gasLimit
)

web3!.eth.sendTransaction(transaction: transaction, options: nil) { result in
    switch result {
    case .success(let txHash):
        print("Transaction sent: \(txHash)")
    case .failure(let error):
        print("Failed to send transaction: \(error.localizedDescription)")
    }
}
```

Querying Transactions:

1. Use the `eth_getTransactionByHash` JSON-RPC method to retrieve transaction details:
   * The method signature: `web3!.eth.getTransactionByHash(txHash: String)`
   * Example usage: `let tx = web3!.eth.getTransactionByHash(txHash: "0xabcdef1234567890")`
   * Handle the response to access the details like sender, receiver, amount, etc.

Please note that the above code snippets provide a general idea of the steps involved in creating a wallet, sending a transaction, and querying transactions using web3 in iOS. Actual implementation may require additional error handling and other modifications based on your specific needs and the Web3Swift library version you are using.
