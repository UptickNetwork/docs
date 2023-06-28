# Events

The nft module emits the following events:

## Handlers

### MsgIssueDenom

| Type         | Attribute Key | Attribute Value  |
| ------------ | ------------- | ---------------- |
| issue\_denom | denom\_id     | {nftDenomID}     |
| issue\_denom | denom\_name   | {nftDenomName}   |
| issue\_denom | creator       | {creatorAddress} |
| message      | module        | nft              |
| message      | sender        | {senderAddress}  |

### MsgTransferNFT

| Type          | Attribute Key | Attribute Value    |
| ------------- | ------------- | ------------------ |
| transfer\_nft | token\_id     | {tokenID}          |
| transfer\_nft | denom\_id     | {nftDenomID}       |
| transfer\_nft | sender        | {senderAddress}    |
| transfer\_nft | recipient     | {recipientAddress} |
| message       | module        | nft                |
| message       | sender        | {senderAddress}    |

### MsgEditNFT

| Type      | Attribute Key | Attribute Value |
| --------- | ------------- | --------------- |
| edit\_nft | token\_id     | {tokenID}       |
| edit\_nft | denom\_id     | {nftDenomID}    |
| edit\_nft | token\_uri    | {tokenURI}      |
| edit\_nft | owner         | {ownerAddress}  |
| message   | module        | nft             |
| message   | sender        | {senderAddress} |

### MsgMintNFT

| Type      | Attribute Key | Attribute Value    |
| --------- | ------------- | ------------------ |
| mint\_nft | token\_id     | {tokenID}          |
| mint\_nft | denom\_id     | {nftDenomID}       |
| mint\_nft | token\_uri    | {tokenURI}         |
| mint\_nft | recipient     | {recipientAddress} |
| message   | module        | nft                |
| message   | sender        | {senderAddress}    |

### MsgBurnNFTs

| Type      | Attribute Key | Attribute Value |
| --------- | ------------- | --------------- |
| burn\_nft | denom\_id     | {nftDenomID}    |
| burn\_nft | token\_id     | {tokenID}       |
| burn\_nft | owner         | {ownerAddress}  |
| message   | module        | nft             |
| message   | sender        | {senderAddress} |

### MsgTransferDenom

| Type            | Attribute Key | Attribute Value    |
| --------------- | ------------- | ------------------ |
| transfer\_denom | denom\_id     | {nftDenomID}       |
| transfer\_denom | sender        | {senderAddress}    |
| transfer\_denom | recipient     | {recipientAddress} |
| message         | module        | nft                |
| message         | sender        | {senderAddress}    |
