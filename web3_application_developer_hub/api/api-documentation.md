# Api interface documentation

**HOST**:https://api.uptick.network

**Version**V.0.1

# Block information interface


## Query transaction block information based on block number


**uri**:`/api/block/getBlock`


**Request Method**:`GET`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|apiKey|Api Key|query|true|string||
|blockNumber|Block number|query|true|integer(int64)||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«Blocks»|
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||Blocks|Blocks|
|&emsp;&emsp;baseFeePerGas||integer(int64)||
|&emsp;&emsp;blockHash||string||
|&emsp;&emsp;consensus||boolean||
|&emsp;&emsp;difficulty||integer(int64)||
|&emsp;&emsp;gasLimit||integer(int64)||
|&emsp;&emsp;gasUsed||integer(int64)||
|&emsp;&emsp;isEmpty||boolean||
|&emsp;&emsp;minerHashHex||string||
|&emsp;&emsp;nonceHex||string||
|&emsp;&emsp;number||integer(int64)||
|&emsp;&emsp;parentHashHex||string||
|&emsp;&emsp;refetchNeeded||boolean||
|&emsp;&emsp;size||integer(int32)||
|&emsp;&emsp;totalDifficulty||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"baseFeePerGas": 0,
		"blockHash": "",
		"consensus": true,
		"difficulty": 0,
		"gasLimit": 0,
		"gasUsed": 0,
		"isEmpty": true,
		"minerHashHex": "",
		"nonceHex": "",
		"number": 0,
		"parentHashHex": "",
		"refetchNeeded": true,
		"size": 0,
		"totalDifficulty": 0
	},
	"msg": "",
	"success": true
}
```


## Query transaction block information based on block number


**uri**:`/api/block/getBlock`


**Request Method**:`POST`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|apiKey|Api Key|query|true|string||
|blockNumber|Block number|query|true|integer(int64)||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«Blocks»|
|201|Created||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||Blocks|Blocks|
|&emsp;&emsp;baseFeePerGas||integer(int64)||
|&emsp;&emsp;blockHash||string||
|&emsp;&emsp;consensus||boolean||
|&emsp;&emsp;difficulty||integer(int64)||
|&emsp;&emsp;gasLimit||integer(int64)||
|&emsp;&emsp;gasUsed||integer(int64)||
|&emsp;&emsp;isEmpty||boolean||
|&emsp;&emsp;minerHashHex||string||
|&emsp;&emsp;nonceHex||string||
|&emsp;&emsp;number||integer(int64)||
|&emsp;&emsp;parentHashHex||string||
|&emsp;&emsp;refetchNeeded||boolean||
|&emsp;&emsp;size||integer(int32)||
|&emsp;&emsp;totalDifficulty||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"baseFeePerGas": 0,
		"blockHash": "",
		"consensus": true,
		"difficulty": 0,
		"gasLimit": 0,
		"gasUsed": 0,
		"isEmpty": true,
		"minerHashHex": "",
		"nonceHex": "",
		"number": 0,
		"parentHashHex": "",
		"refetchNeeded": true,
		"size": 0,
		"totalDifficulty": 0
	},
	"msg": "",
	"success": true
}
```


## Query transaction block information based on block hash


**uri**:`/api/block/getBlockByHash`


**Request Method**:`GET`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|apiKey|Api Key|query|true|string||
|blockHash|Block tx hash|query|true|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«Blocks»|
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||Blocks|Blocks|
|&emsp;&emsp;baseFeePerGas||integer(int64)||
|&emsp;&emsp;blockHash||string||
|&emsp;&emsp;consensus||boolean||
|&emsp;&emsp;difficulty||integer(int64)||
|&emsp;&emsp;gasLimit||integer(int64)||
|&emsp;&emsp;gasUsed||integer(int64)||
|&emsp;&emsp;isEmpty||boolean||
|&emsp;&emsp;minerHashHex||string||
|&emsp;&emsp;nonceHex||string||
|&emsp;&emsp;number||integer(int64)||
|&emsp;&emsp;parentHashHex||string||
|&emsp;&emsp;refetchNeeded||boolean||
|&emsp;&emsp;size||integer(int32)||
|&emsp;&emsp;totalDifficulty||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"baseFeePerGas": 0,
		"blockHash": "",
		"consensus": true,
		"difficulty": 0,
		"gasLimit": 0,
		"gasUsed": 0,
		"isEmpty": true,
		"minerHashHex": "",
		"nonceHex": "",
		"number": 0,
		"parentHashHex": "",
		"refetchNeeded": true,
		"size": 0,
		"totalDifficulty": 0
	},
	"msg": "",
	"success": true
}
```


## Query transaction block information based on block hash


**uri**:`/api/block/getBlockByHash`


**Request Method**:`POST`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|apiKey|Api Key|query|true|string||
|blockHash|Block tx hash|query|true|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«Blocks»|
|201|Created||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||Blocks|Blocks|
|&emsp;&emsp;baseFeePerGas||integer(int64)||
|&emsp;&emsp;blockHash||string||
|&emsp;&emsp;consensus||boolean||
|&emsp;&emsp;difficulty||integer(int64)||
|&emsp;&emsp;gasLimit||integer(int64)||
|&emsp;&emsp;gasUsed||integer(int64)||
|&emsp;&emsp;isEmpty||boolean||
|&emsp;&emsp;minerHashHex||string||
|&emsp;&emsp;nonceHex||string||
|&emsp;&emsp;number||integer(int64)||
|&emsp;&emsp;parentHashHex||string||
|&emsp;&emsp;refetchNeeded||boolean||
|&emsp;&emsp;size||integer(int32)||
|&emsp;&emsp;totalDifficulty||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"baseFeePerGas": 0,
		"blockHash": "",
		"consensus": true,
		"difficulty": 0,
		"gasLimit": 0,
		"gasUsed": 0,
		"isEmpty": true,
		"minerHashHex": "",
		"nonceHex": "",
		"number": 0,
		"parentHashHex": "",
		"refetchNeeded": true,
		"size": 0,
		"totalDifficulty": 0
	},
	"msg": "",
	"success": true
}
```


# Transaction information interface


## Query transaction information based on txhash


**uri**:`/api/transaction/txByHash`


**Request Method**:`GET`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|apiKey|Api Key|query|true|string||
|hash|Tx hash|query|true|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«Transactions»|
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||Transactions|Transactions|
|&emsp;&emsp;blockHashHex||string||
|&emsp;&emsp;blockNumber||integer(int32)||
|&emsp;&emsp;createdContractAddress||string||
|&emsp;&emsp;createdContractCodeIndexedAt||string(date-time)||
|&emsp;&emsp;cumulativeGasUsed||integer(int64)||
|&emsp;&emsp;earliestProcessingStart||string(date-time)||
|&emsp;&emsp;error||string||
|&emsp;&emsp;fromAddress||string||
|&emsp;&emsp;gas||integer(int64)||
|&emsp;&emsp;gasPrice||integer(int64)||
|&emsp;&emsp;gasUsed||integer(int64)||
|&emsp;&emsp;hasErrorInInternalTxs||boolean||
|&emsp;&emsp;index||integer(int32)||
|&emsp;&emsp;inputHex||string||
|&emsp;&emsp;maxFeePerGas||integer(int64)||
|&emsp;&emsp;maxPriorityFeePerGas||integer(int64)||
|&emsp;&emsp;nonce||integer(int32)||
|&emsp;&emsp;oldBlockHashHex||string||
|&emsp;&emsp;r||string||
|&emsp;&emsp;revertReason||string||
|&emsp;&emsp;s||string||
|&emsp;&emsp;status||integer(int32)||
|&emsp;&emsp;toAddress||string||
|&emsp;&emsp;transactionsHash||string||
|&emsp;&emsp;type||integer(int32)||
|&emsp;&emsp;v||string||
|&emsp;&emsp;value||number(bigdecimal)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"blockHashHex": "",
		"blockNumber": 0,
		"createdContractAddress": "",
		"createdContractCodeIndexedAt": "",
		"cumulativeGasUsed": 0,
		"earliestProcessingStart": "",
		"error": "",
		"fromAddress": "",
		"gas": 0,
		"gasPrice": 0,
		"gasUsed": 0,
		"hasErrorInInternalTxs": true,
		"index": 0,
		"inputHex": "",
		"maxFeePerGas": 0,
		"maxPriorityFeePerGas": 0,
		"nonce": 0,
		"oldBlockHashHex": "",
		"r": "",
		"revertReason": "",
		"s": "",
		"status": 0,
		"toAddress": "",
		"transactionsHash": "",
		"type": 0,
		"v": "",
		"value": 0
	},
	"msg": "",
	"success": true
}
```


## Query transaction information based on txhash


**uri**:`/api/transaction/txByHash`


**Request Method**:`POST`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|apiKey|Api Key|query|true|string||
|hash|Tx hash|query|true|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«Transactions»|
|201|Created||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||Transactions|Transactions|
|&emsp;&emsp;blockHashHex||string||
|&emsp;&emsp;blockNumber||integer(int32)||
|&emsp;&emsp;createdContractAddress||string||
|&emsp;&emsp;createdContractCodeIndexedAt||string(date-time)||
|&emsp;&emsp;cumulativeGasUsed||integer(int64)||
|&emsp;&emsp;earliestProcessingStart||string(date-time)||
|&emsp;&emsp;error||string||
|&emsp;&emsp;fromAddress||string||
|&emsp;&emsp;gas||integer(int64)||
|&emsp;&emsp;gasPrice||integer(int64)||
|&emsp;&emsp;gasUsed||integer(int64)||
|&emsp;&emsp;hasErrorInInternalTxs||boolean||
|&emsp;&emsp;index||integer(int32)||
|&emsp;&emsp;inputHex||string||
|&emsp;&emsp;maxFeePerGas||integer(int64)||
|&emsp;&emsp;maxPriorityFeePerGas||integer(int64)||
|&emsp;&emsp;nonce||integer(int32)||
|&emsp;&emsp;oldBlockHashHex||string||
|&emsp;&emsp;r||string||
|&emsp;&emsp;revertReason||string||
|&emsp;&emsp;s||string||
|&emsp;&emsp;status||integer(int32)||
|&emsp;&emsp;toAddress||string||
|&emsp;&emsp;transactionsHash||string||
|&emsp;&emsp;type||integer(int32)||
|&emsp;&emsp;v||string||
|&emsp;&emsp;value||number(bigdecimal)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"blockHashHex": "",
		"blockNumber": 0,
		"createdContractAddress": "",
		"createdContractCodeIndexedAt": "",
		"cumulativeGasUsed": 0,
		"earliestProcessingStart": "",
		"error": "",
		"fromAddress": "",
		"gas": 0,
		"gasPrice": 0,
		"gasUsed": 0,
		"hasErrorInInternalTxs": true,
		"index": 0,
		"inputHex": "",
		"maxFeePerGas": 0,
		"maxPriorityFeePerGas": 0,
		"nonce": 0,
		"oldBlockHashHex": "",
		"r": "",
		"revertReason": "",
		"s": "",
		"status": 0,
		"toAddress": "",
		"transactionsHash": "",
		"type": 0,
		"v": "",
		"value": 0
	},
	"msg": "",
	"success": true
}
```


## Query transaction information based on txhash


**uri**:`/api/transaction/txInternalByHash`


**Request Method**:`GET`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|apiKey|Api Key|query|true|string||
|hash|Tx hash|query|true|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«InternalTransactions»|
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||InternalTransactions|InternalTransactions|
|&emsp;&emsp;blockHashHex||string||
|&emsp;&emsp;blockIndex||integer(int32)||
|&emsp;&emsp;blockNumber||integer(int32)||
|&emsp;&emsp;callType||string||
|&emsp;&emsp;createdContractAddress||string||
|&emsp;&emsp;createdContractCodeHex||string||
|&emsp;&emsp;error||string||
|&emsp;&emsp;fromAddress||string||
|&emsp;&emsp;gas||integer(int64)||
|&emsp;&emsp;gasUsed||integer(int64)||
|&emsp;&emsp;index||integer(int32)||
|&emsp;&emsp;initHex||string||
|&emsp;&emsp;inputHex||string||
|&emsp;&emsp;insertedAt||string(date-time)||
|&emsp;&emsp;outputHex||string||
|&emsp;&emsp;toAddress||string||
|&emsp;&emsp;transactionHashHex||string||
|&emsp;&emsp;transactionIndex||integer(int32)||
|&emsp;&emsp;type||string||
|&emsp;&emsp;updatedAt||string(date-time)||
|&emsp;&emsp;value||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"blockHashHex": "",
		"blockIndex": 0,
		"blockNumber": 0,
		"callType": "",
		"createdContractAddress": "",
		"createdContractCodeHex": "",
		"error": "",
		"fromAddress": "",
		"gas": 0,
		"gasUsed": 0,
		"index": 0,
		"initHex": "",
		"inputHex": "",
		"insertedAt": "",
		"outputHex": "",
		"toAddress": "",
		"transactionHashHex": "",
		"transactionIndex": 0,
		"type": "",
		"updatedAt": "",
		"value": 0
	},
	"msg": "",
	"success": true
}
```


## Query transaction information based on txhash


**uri**:`/api/transaction/txInternalByHash`


**Request Method**:`POST`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|apiKey|Api Key|query|true|string||
|hash|Tx hash|query|true|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«InternalTransactions»|
|201|Created||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||InternalTransactions|InternalTransactions|
|&emsp;&emsp;blockHashHex||string||
|&emsp;&emsp;blockIndex||integer(int32)||
|&emsp;&emsp;blockNumber||integer(int32)||
|&emsp;&emsp;callType||string||
|&emsp;&emsp;createdContractAddress||string||
|&emsp;&emsp;createdContractCodeHex||string||
|&emsp;&emsp;error||string||
|&emsp;&emsp;fromAddress||string||
|&emsp;&emsp;gas||integer(int64)||
|&emsp;&emsp;gasUsed||integer(int64)||
|&emsp;&emsp;index||integer(int32)||
|&emsp;&emsp;initHex||string||
|&emsp;&emsp;inputHex||string||
|&emsp;&emsp;insertedAt||string(date-time)||
|&emsp;&emsp;outputHex||string||
|&emsp;&emsp;toAddress||string||
|&emsp;&emsp;transactionHashHex||string||
|&emsp;&emsp;transactionIndex||integer(int32)||
|&emsp;&emsp;type||string||
|&emsp;&emsp;updatedAt||string(date-time)||
|&emsp;&emsp;value||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"blockHashHex": "",
		"blockIndex": 0,
		"blockNumber": 0,
		"callType": "",
		"createdContractAddress": "",
		"createdContractCodeHex": "",
		"error": "",
		"fromAddress": "",
		"gas": 0,
		"gasUsed": 0,
		"index": 0,
		"initHex": "",
		"inputHex": "",
		"insertedAt": "",
		"outputHex": "",
		"toAddress": "",
		"transactionHashHex": "",
		"transactionIndex": 0,
		"type": "",
		"updatedAt": "",
		"value": 0
	},
	"msg": "",
	"success": true
}
```


# User Information Interface


## Query address balance


**uri**:`/api/account/balance`


**Request Method**:`GET`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«string»|
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||string||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": "",
	"msg": "",
	"success": true
}
```


## Query address balance


**uri**:`/api/account/balance`


**Request Method**:`POST`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«string»|
|201|Created||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||string||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": "",
	"msg": "",
	"success": true
}
```


## Query the number of tokens owned by the address


**uri**:`/api/account/tokenBalance`


**Request Method**:`GET`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||
|contractAddress|Token contract address|query|false|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«List«TokenBalance»»|
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||array|TokenBalance|
|&emsp;&emsp;contractAddress||string||
|&emsp;&emsp;creator||string||
|&emsp;&emsp;decimals||string||
|&emsp;&emsp;name||string||
|&emsp;&emsp;owner||string||
|&emsp;&emsp;symbol||string||
|&emsp;&emsp;tokens||array|TokenIdDto|
|&emsp;&emsp;&emsp;&emsp;balance||number||
|&emsp;&emsp;&emsp;&emsp;tokenId||string||
|&emsp;&emsp;type||string||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": [
		{
			"contractAddress": "",
			"creator": "",
			"decimals": "",
			"name": "",
			"owner": "",
			"symbol": "",
			"tokens": [
				{
					"balance": 0,
					"tokenId": ""
				}
			],
			"type": ""
		}
	],
	"msg": "",
	"success": true
}
```


## Query the number of tokens owned by the address


**uri**:`/api/account/tokenBalance`


**Request Method**:`POST`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||
|contractAddress|Token contract address|query|false|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«List«TokenBalance»»|
|201|Created||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||array|TokenBalance|
|&emsp;&emsp;contractAddress||string||
|&emsp;&emsp;creator||string||
|&emsp;&emsp;decimals||string||
|&emsp;&emsp;name||string||
|&emsp;&emsp;owner||string||
|&emsp;&emsp;symbol||string||
|&emsp;&emsp;tokens||array|TokenIdDto|
|&emsp;&emsp;&emsp;&emsp;balance||number||
|&emsp;&emsp;&emsp;&emsp;tokenId||string||
|&emsp;&emsp;type||string||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": [
		{
			"contractAddress": "",
			"creator": "",
			"decimals": "",
			"name": "",
			"owner": "",
			"symbol": "",
			"tokens": [
				{
					"balance": 0,
					"tokenId": ""
				}
			],
			"type": ""
		}
	],
	"msg": "",
	"success": true
}
```


## The total number of tokens owned by the query address


**uri**:`/api/account/tokenList`


**Request Method**:`GET`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«List«TokenListDto»»|
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||array|TokenListDto|
|&emsp;&emsp;balance||number(bigdecimal)||
|&emsp;&emsp;contractAddress||string||
|&emsp;&emsp;creator||string||
|&emsp;&emsp;decimals||string||
|&emsp;&emsp;name||string||
|&emsp;&emsp;owner||string||
|&emsp;&emsp;symbol||string||
|&emsp;&emsp;type||string||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": [
		{
			"balance": 0,
			"contractAddress": "",
			"creator": "",
			"decimals": "",
			"name": "",
			"owner": "",
			"symbol": "",
			"type": ""
		}
	],
	"msg": "",
	"success": true
}
```


## The total number of tokens owned by the query address


**uri**:`/api/account/tokenList`


**Request Method**:`POST`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«List«TokenListDto»»|
|201|Created||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||array|TokenListDto|
|&emsp;&emsp;balance||number(bigdecimal)||
|&emsp;&emsp;contractAddress||string||
|&emsp;&emsp;creator||string||
|&emsp;&emsp;decimals||string||
|&emsp;&emsp;name||string||
|&emsp;&emsp;owner||string||
|&emsp;&emsp;symbol||string||
|&emsp;&emsp;type||string||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": [
		{
			"balance": 0,
			"contractAddress": "",
			"creator": "",
			"decimals": "",
			"name": "",
			"owner": "",
			"symbol": "",
			"type": ""
		}
	],
	"msg": "",
	"success": true
}
```


## Query token transaction information based on wallet address


**uri**:`/api/account/tokenTxList`


**Request Method**:`GET`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||
|tokenContractAddress|Token contract address|query|true|string||
|pageNumber|page number|query|false|integer(int32)||
|pageSize|Number of entries per page|query|false|integer(int32)||
|sort|Sort Rule (desc | asc)|query|false|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«PageQuery«TokenTransfers»»|
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||PageQuery«TokenTransfers»|PageQuery«TokenTransfers»|
|&emsp;&emsp;firstPage||boolean||
|&emsp;&emsp;lastPage||boolean||
|&emsp;&emsp;list||array|TokenTransfers|
|&emsp;&emsp;&emsp;&emsp;amount||number||
|&emsp;&emsp;&emsp;&emsp;blockHashHex||string||
|&emsp;&emsp;&emsp;&emsp;blockNumber||integer||
|&emsp;&emsp;&emsp;&emsp;fromAddress||string||
|&emsp;&emsp;&emsp;&emsp;logIndex||integer||
|&emsp;&emsp;&emsp;&emsp;toAddress||string||
|&emsp;&emsp;&emsp;&emsp;tokenContractAddress||string||
|&emsp;&emsp;&emsp;&emsp;tokenId||string||
|&emsp;&emsp;&emsp;&emsp;transactionHashHex||string||
|&emsp;&emsp;orderBy||string||
|&emsp;&emsp;pageNumber||integer(int64)||
|&emsp;&emsp;pageSize||integer(int64)||
|&emsp;&emsp;paras||object||
|&emsp;&emsp;totalPage||integer(int64)||
|&emsp;&emsp;totalRow||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"firstPage": true,
		"lastPage": true,
		"list": [
			{
				"amount": 0,
				"blockHashHex": "",
				"blockNumber": 0,
				"fromAddress": "",
				"logIndex": 0,
				"toAddress": "",
				"tokenContractAddress": "",
				"tokenId": "",
				"transactionHashHex": ""
			}
		],
		"orderBy": "",
		"pageNumber": 0,
		"pageSize": 0,
		"paras": {},
		"totalPage": 0,
		"totalRow": 0
	},
	"msg": "",
	"success": true
}
```


## Query token transaction information based on wallet address


**uri**:`/api/account/tokenTxList`


**Request Method**:`POST`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||
|tokenContractAddress|Token contract address|query|true|string||
|pageNumber|page number|query|false|integer(int32)||
|pageSize|Number of entries per page|query|false|integer(int32)||
|sort|Sort Rule (desc | asc)|query|false|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«PageQuery«TokenTransfers»»|
|201|Created||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||PageQuery«TokenTransfers»|PageQuery«TokenTransfers»|
|&emsp;&emsp;firstPage||boolean||
|&emsp;&emsp;lastPage||boolean||
|&emsp;&emsp;list||array|TokenTransfers|
|&emsp;&emsp;&emsp;&emsp;amount||number||
|&emsp;&emsp;&emsp;&emsp;blockHashHex||string||
|&emsp;&emsp;&emsp;&emsp;blockNumber||integer||
|&emsp;&emsp;&emsp;&emsp;fromAddress||string||
|&emsp;&emsp;&emsp;&emsp;logIndex||integer||
|&emsp;&emsp;&emsp;&emsp;toAddress||string||
|&emsp;&emsp;&emsp;&emsp;tokenContractAddress||string||
|&emsp;&emsp;&emsp;&emsp;tokenId||string||
|&emsp;&emsp;&emsp;&emsp;transactionHashHex||string||
|&emsp;&emsp;orderBy||string||
|&emsp;&emsp;pageNumber||integer(int64)||
|&emsp;&emsp;pageSize||integer(int64)||
|&emsp;&emsp;paras||object||
|&emsp;&emsp;totalPage||integer(int64)||
|&emsp;&emsp;totalRow||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"firstPage": true,
		"lastPage": true,
		"list": [
			{
				"amount": 0,
				"blockHashHex": "",
				"blockNumber": 0,
				"fromAddress": "",
				"logIndex": 0,
				"toAddress": "",
				"tokenContractAddress": "",
				"tokenId": "",
				"transactionHashHex": ""
			}
		],
		"orderBy": "",
		"pageNumber": 0,
		"pageSize": 0,
		"paras": {},
		"totalPage": 0,
		"totalRow": 0
	},
	"msg": "",
	"success": true
}
```


## Query transaction information based on wallet address


**uri**:`/api/account/txList`


**Request Method**:`GET`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||
|pageNumber|page number|query|false|integer(int32)||
|pageSize|Number of entries per page|query|false|integer(int32)||
|sort|Sort Rule (desc | asc)|query|false|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«PageQuery«Transactions»»|
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||PageQuery«Transactions»|PageQuery«Transactions»|
|&emsp;&emsp;firstPage||boolean||
|&emsp;&emsp;lastPage||boolean||
|&emsp;&emsp;list||array|Transactions|
|&emsp;&emsp;&emsp;&emsp;blockHashHex||string||
|&emsp;&emsp;&emsp;&emsp;blockNumber||integer||
|&emsp;&emsp;&emsp;&emsp;createdContractAddress||string||
|&emsp;&emsp;&emsp;&emsp;createdContractCodeIndexedAt||string||
|&emsp;&emsp;&emsp;&emsp;cumulativeGasUsed||integer||
|&emsp;&emsp;&emsp;&emsp;earliestProcessingStart||string||
|&emsp;&emsp;&emsp;&emsp;error||string||
|&emsp;&emsp;&emsp;&emsp;fromAddress||string||
|&emsp;&emsp;&emsp;&emsp;gas||integer||
|&emsp;&emsp;&emsp;&emsp;gasPrice||integer||
|&emsp;&emsp;&emsp;&emsp;gasUsed||integer||
|&emsp;&emsp;&emsp;&emsp;hasErrorInInternalTxs||boolean||
|&emsp;&emsp;&emsp;&emsp;index||integer||
|&emsp;&emsp;&emsp;&emsp;inputHex||string||
|&emsp;&emsp;&emsp;&emsp;maxFeePerGas||integer||
|&emsp;&emsp;&emsp;&emsp;maxPriorityFeePerGas||integer||
|&emsp;&emsp;&emsp;&emsp;nonce||integer||
|&emsp;&emsp;&emsp;&emsp;oldBlockHashHex||string||
|&emsp;&emsp;&emsp;&emsp;r||string||
|&emsp;&emsp;&emsp;&emsp;revertReason||string||
|&emsp;&emsp;&emsp;&emsp;s||string||
|&emsp;&emsp;&emsp;&emsp;status||integer||
|&emsp;&emsp;&emsp;&emsp;toAddress||string||
|&emsp;&emsp;&emsp;&emsp;transactionsHash||string||
|&emsp;&emsp;&emsp;&emsp;type||integer||
|&emsp;&emsp;&emsp;&emsp;v||string||
|&emsp;&emsp;&emsp;&emsp;value||number||
|&emsp;&emsp;orderBy||string||
|&emsp;&emsp;pageNumber||integer(int64)||
|&emsp;&emsp;pageSize||integer(int64)||
|&emsp;&emsp;paras||object||
|&emsp;&emsp;totalPage||integer(int64)||
|&emsp;&emsp;totalRow||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"firstPage": true,
		"lastPage": true,
		"list": [
			{
				"blockHashHex": "",
				"blockNumber": 0,
				"createdContractAddress": "",
				"createdContractCodeIndexedAt": "",
				"cumulativeGasUsed": 0,
				"earliestProcessingStart": "",
				"error": "",
				"fromAddress": "",
				"gas": 0,
				"gasPrice": 0,
				"gasUsed": 0,
				"hasErrorInInternalTxs": true,
				"index": 0,
				"inputHex": "",
				"maxFeePerGas": 0,
				"maxPriorityFeePerGas": 0,
				"nonce": 0,
				"oldBlockHashHex": "",
				"r": "",
				"revertReason": "",
				"s": "",
				"status": 0,
				"toAddress": "",
				"transactionsHash": "",
				"type": 0,
				"v": "",
				"value": 0
			}
		],
		"orderBy": "",
		"pageNumber": 0,
		"pageSize": 0,
		"paras": {},
		"totalPage": 0,
		"totalRow": 0
	},
	"msg": "",
	"success": true
}
```


## Query transaction information based on wallet address


**uri**:`/api/account/txList`


**Request Method**:`POST`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||
|pageNumber|page number|query|false|integer(int32)||
|pageSize|Number of entries per page|query|false|integer(int32)||
|sort|Sort Rule (desc | asc)|query|false|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«PageQuery«Transactions»»|
|201|Created||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||PageQuery«Transactions»|PageQuery«Transactions»|
|&emsp;&emsp;firstPage||boolean||
|&emsp;&emsp;lastPage||boolean||
|&emsp;&emsp;list||array|Transactions|
|&emsp;&emsp;&emsp;&emsp;blockHashHex||string||
|&emsp;&emsp;&emsp;&emsp;blockNumber||integer||
|&emsp;&emsp;&emsp;&emsp;createdContractAddress||string||
|&emsp;&emsp;&emsp;&emsp;createdContractCodeIndexedAt||string||
|&emsp;&emsp;&emsp;&emsp;cumulativeGasUsed||integer||
|&emsp;&emsp;&emsp;&emsp;earliestProcessingStart||string||
|&emsp;&emsp;&emsp;&emsp;error||string||
|&emsp;&emsp;&emsp;&emsp;fromAddress||string||
|&emsp;&emsp;&emsp;&emsp;gas||integer||
|&emsp;&emsp;&emsp;&emsp;gasPrice||integer||
|&emsp;&emsp;&emsp;&emsp;gasUsed||integer||
|&emsp;&emsp;&emsp;&emsp;hasErrorInInternalTxs||boolean||
|&emsp;&emsp;&emsp;&emsp;index||integer||
|&emsp;&emsp;&emsp;&emsp;inputHex||string||
|&emsp;&emsp;&emsp;&emsp;maxFeePerGas||integer||
|&emsp;&emsp;&emsp;&emsp;maxPriorityFeePerGas||integer||
|&emsp;&emsp;&emsp;&emsp;nonce||integer||
|&emsp;&emsp;&emsp;&emsp;oldBlockHashHex||string||
|&emsp;&emsp;&emsp;&emsp;r||string||
|&emsp;&emsp;&emsp;&emsp;revertReason||string||
|&emsp;&emsp;&emsp;&emsp;s||string||
|&emsp;&emsp;&emsp;&emsp;status||integer||
|&emsp;&emsp;&emsp;&emsp;toAddress||string||
|&emsp;&emsp;&emsp;&emsp;transactionsHash||string||
|&emsp;&emsp;&emsp;&emsp;type||integer||
|&emsp;&emsp;&emsp;&emsp;v||string||
|&emsp;&emsp;&emsp;&emsp;value||number||
|&emsp;&emsp;orderBy||string||
|&emsp;&emsp;pageNumber||integer(int64)||
|&emsp;&emsp;pageSize||integer(int64)||
|&emsp;&emsp;paras||object||
|&emsp;&emsp;totalPage||integer(int64)||
|&emsp;&emsp;totalRow||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"firstPage": true,
		"lastPage": true,
		"list": [
			{
				"blockHashHex": "",
				"blockNumber": 0,
				"createdContractAddress": "",
				"createdContractCodeIndexedAt": "",
				"cumulativeGasUsed": 0,
				"earliestProcessingStart": "",
				"error": "",
				"fromAddress": "",
				"gas": 0,
				"gasPrice": 0,
				"gasUsed": 0,
				"hasErrorInInternalTxs": true,
				"index": 0,
				"inputHex": "",
				"maxFeePerGas": 0,
				"maxPriorityFeePerGas": 0,
				"nonce": 0,
				"oldBlockHashHex": "",
				"r": "",
				"revertReason": "",
				"s": "",
				"status": 0,
				"toAddress": "",
				"transactionsHash": "",
				"type": 0,
				"v": "",
				"value": 0
			}
		],
		"orderBy": "",
		"pageNumber": 0,
		"pageSize": 0,
		"paras": {},
		"totalPage": 0,
		"totalRow": 0
	},
	"msg": "",
	"success": true
}
```


## Query Internal transaction information based on wallet address


**uri**:`/api/account/txListInternal`


**Request Method**:`GET`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||
|pageNumber|page number|query|false|integer(int32)||
|pageSize|Number of entries per page|query|false|integer(int32)||
|sort|Sort Rule (desc | asc)|query|false|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«PageQuery«InternalTransactions»»|
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||PageQuery«InternalTransactions»|PageQuery«InternalTransactions»|
|&emsp;&emsp;firstPage||boolean||
|&emsp;&emsp;lastPage||boolean||
|&emsp;&emsp;list||array|InternalTransactions|
|&emsp;&emsp;&emsp;&emsp;blockHashHex||string||
|&emsp;&emsp;&emsp;&emsp;blockIndex||integer||
|&emsp;&emsp;&emsp;&emsp;blockNumber||integer||
|&emsp;&emsp;&emsp;&emsp;callType||string||
|&emsp;&emsp;&emsp;&emsp;createdContractAddress||string||
|&emsp;&emsp;&emsp;&emsp;createdContractCodeHex||string||
|&emsp;&emsp;&emsp;&emsp;error||string||
|&emsp;&emsp;&emsp;&emsp;fromAddress||string||
|&emsp;&emsp;&emsp;&emsp;gas||integer||
|&emsp;&emsp;&emsp;&emsp;gasUsed||integer||
|&emsp;&emsp;&emsp;&emsp;index||integer||
|&emsp;&emsp;&emsp;&emsp;initHex||string||
|&emsp;&emsp;&emsp;&emsp;inputHex||string||
|&emsp;&emsp;&emsp;&emsp;insertedAt||string||
|&emsp;&emsp;&emsp;&emsp;outputHex||string||
|&emsp;&emsp;&emsp;&emsp;toAddress||string||
|&emsp;&emsp;&emsp;&emsp;transactionHashHex||string||
|&emsp;&emsp;&emsp;&emsp;transactionIndex||integer||
|&emsp;&emsp;&emsp;&emsp;type||string||
|&emsp;&emsp;&emsp;&emsp;updatedAt||string||
|&emsp;&emsp;&emsp;&emsp;value||integer||
|&emsp;&emsp;orderBy||string||
|&emsp;&emsp;pageNumber||integer(int64)||
|&emsp;&emsp;pageSize||integer(int64)||
|&emsp;&emsp;paras||object||
|&emsp;&emsp;totalPage||integer(int64)||
|&emsp;&emsp;totalRow||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"firstPage": true,
		"lastPage": true,
		"list": [
			{
				"blockHashHex": "",
				"blockIndex": 0,
				"blockNumber": 0,
				"callType": "",
				"createdContractAddress": "",
				"createdContractCodeHex": "",
				"error": "",
				"fromAddress": "",
				"gas": 0,
				"gasUsed": 0,
				"index": 0,
				"initHex": "",
				"inputHex": "",
				"insertedAt": "",
				"outputHex": "",
				"toAddress": "",
				"transactionHashHex": "",
				"transactionIndex": 0,
				"type": "",
				"updatedAt": "",
				"value": 0
			}
		],
		"orderBy": "",
		"pageNumber": 0,
		"pageSize": 0,
		"paras": {},
		"totalPage": 0,
		"totalRow": 0
	},
	"msg": "",
	"success": true
}
```


## Query Internal transaction information based on wallet address


**uri**:`/api/account/txListInternal`


**Request Method**:`POST`


**Request Data Type**:`application/x-www-form-urlencoded`


**Response Data Type**:`*/*`





**Request parameters**:


| Parameter | Parameter Description | Request type    | Required | Data type | schema |
| -------- | -------- | ----- | -------- | -------- | ------ |
|address|Wallet address|query|true|string||
|apiKey|Api Key|query|true|string||
|pageNumber|page number|query|false|integer(int32)||
|pageSize|Number of entries per page|query|false|integer(int32)||
|sort|Sort Rule (desc | asc)|query|false|string||


**Response Status**:


| Status | Illustrate | schema |
| -------- | -------- | ----- | 
|200|OK|JsonResult«PageQuery«InternalTransactions»»|
|201|Created||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||


**Response parameters**:


| Parameter | Parameter Description | Types  | schema |
| -------- | -------- | ----- |----- | 
|code||integer(int32)|integer(int32)|
|data||PageQuery«InternalTransactions»|PageQuery«InternalTransactions»|
|&emsp;&emsp;firstPage||boolean||
|&emsp;&emsp;lastPage||boolean||
|&emsp;&emsp;list||array|InternalTransactions|
|&emsp;&emsp;&emsp;&emsp;blockHashHex||string||
|&emsp;&emsp;&emsp;&emsp;blockIndex||integer||
|&emsp;&emsp;&emsp;&emsp;blockNumber||integer||
|&emsp;&emsp;&emsp;&emsp;callType||string||
|&emsp;&emsp;&emsp;&emsp;createdContractAddress||string||
|&emsp;&emsp;&emsp;&emsp;createdContractCodeHex||string||
|&emsp;&emsp;&emsp;&emsp;error||string||
|&emsp;&emsp;&emsp;&emsp;fromAddress||string||
|&emsp;&emsp;&emsp;&emsp;gas||integer||
|&emsp;&emsp;&emsp;&emsp;gasUsed||integer||
|&emsp;&emsp;&emsp;&emsp;index||integer||
|&emsp;&emsp;&emsp;&emsp;initHex||string||
|&emsp;&emsp;&emsp;&emsp;inputHex||string||
|&emsp;&emsp;&emsp;&emsp;insertedAt||string||
|&emsp;&emsp;&emsp;&emsp;outputHex||string||
|&emsp;&emsp;&emsp;&emsp;toAddress||string||
|&emsp;&emsp;&emsp;&emsp;transactionHashHex||string||
|&emsp;&emsp;&emsp;&emsp;transactionIndex||integer||
|&emsp;&emsp;&emsp;&emsp;type||string||
|&emsp;&emsp;&emsp;&emsp;updatedAt||string||
|&emsp;&emsp;&emsp;&emsp;value||integer||
|&emsp;&emsp;orderBy||string||
|&emsp;&emsp;pageNumber||integer(int64)||
|&emsp;&emsp;pageSize||integer(int64)||
|&emsp;&emsp;paras||object||
|&emsp;&emsp;totalPage||integer(int64)||
|&emsp;&emsp;totalRow||integer(int64)||
|msg||string||
|success||boolean||


**Response Example**:
```javascript
{
	"code": 0,
	"data": {
		"firstPage": true,
		"lastPage": true,
		"list": [
			{
				"blockHashHex": "",
				"blockIndex": 0,
				"blockNumber": 0,
				"callType": "",
				"createdContractAddress": "",
				"createdContractCodeHex": "",
				"error": "",
				"fromAddress": "",
				"gas": 0,
				"gasUsed": 0,
				"index": 0,
				"initHex": "",
				"inputHex": "",
				"insertedAt": "",
				"outputHex": "",
				"toAddress": "",
				"transactionHashHex": "",
				"transactionIndex": 0,
				"type": "",
				"updatedAt": "",
				"value": 0
			}
		],
		"orderBy": "",
		"pageNumber": 0,
		"pageSize": 0,
		"paras": {},
		"totalPage": 0,
		"totalRow": 0
	},
	"msg": "",
	"success": true
}
```