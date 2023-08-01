# Api interface

## Api interface documentation

**HOST**:https://api.uptick.network

**Version:**V.0.1

## Block information interface

### Query transaction block information based on block number

**uri**:`/api/block/getBlock`

**Request Method**:`GET`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter   | Parameter Description | Request type | Required | Data type      | schema |
| ----------- | --------------------- | ------------ | -------- | -------------- | ------ |
| apiKey      | Api Key               | query        | true     | string         |        |
| blockNumber | Block number          | query        | true     | integer(int64) |        |

**Response Status**:

| Status | Illustrate   | schema             |
| ------ | ------------ | ------------------ |
| 200    | OK           | JsonResult«Blocks» |
| 401    | Unauthorized |                    |
| 403    | Forbidden    |                    |
| 404    | Not Found    |                    |

**Response parameters**:

| Parameter         | Parameter Description | Types          | schema |
| ----------------- | --------------------- | -------------- | ------ |
| code              | integer(int32)        | integer(int32) |        |
| data              | Blocks                | Blocks         |        |
|   baseFeePerGas   | integer(int64)        |                |        |
|   blockHash       | string                |                |        |
|   consensus       | boolean               |                |        |
|   difficulty      | integer(int64)        |                |        |
|   gasLimit        | integer(int64)        |                |        |
|   gasUsed         | integer(int64)        |                |        |
|   isEmpty         | boolean               |                |        |
|   minerHashHex    | string                |                |        |
|   nonceHex        | string                |                |        |
|   number          | integer(int64)        |                |        |
|   parentHashHex   | string                |                |        |
|   refetchNeeded   | boolean               |                |        |
|   size            | integer(int32)        |                |        |
|   totalDifficulty | integer(int64)        |                |        |
| msg               | string                |                |        |
| success           | boolean               |                |        |

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

### Query transaction block information based on block number

**uri**:`/api/block/getBlock`

**Request Method**:`POST`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter   | Parameter Description | Request type | Required | Data type      | schema |
| ----------- | --------------------- | ------------ | -------- | -------------- | ------ |
| apiKey      | Api Key               | query        | true     | string         |        |
| blockNumber | Block number          | query        | true     | integer(int64) |        |

**Response Status**:

| Status | Illustrate   | schema             |
| ------ | ------------ | ------------------ |
| 200    | OK           | JsonResult«Blocks» |
| 201    | Created      |                    |
| 401    | Unauthorized |                    |
| 403    | Forbidden    |                    |
| 404    | Not Found    |                    |

**Response parameters**:

| Parameter         | Parameter Description | Types          | schema |
| ----------------- | --------------------- | -------------- | ------ |
| code              | integer(int32)        | integer(int32) |        |
| data              | Blocks                | Blocks         |        |
|   baseFeePerGas   | integer(int64)        |                |        |
|   blockHash       | string                |                |        |
|   consensus       | boolean               |                |        |
|   difficulty      | integer(int64)        |                |        |
|   gasLimit        | integer(int64)        |                |        |
|   gasUsed         | integer(int64)        |                |        |
|   isEmpty         | boolean               |                |        |
|   minerHashHex    | string                |                |        |
|   nonceHex        | string                |                |        |
|   number          | integer(int64)        |                |        |
|   parentHashHex   | string                |                |        |
|   refetchNeeded   | boolean               |                |        |
|   size            | integer(int32)        |                |        |
|   totalDifficulty | integer(int64)        |                |        |
| msg               | string                |                |        |
| success           | boolean               |                |        |

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

### Query transaction block information based on block hash

**uri**:`/api/block/getBlockByHash`

**Request Method**:`GET`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter | Parameter Description | Request type | Required | Data type | schema |
| --------- | --------------------- | ------------ | -------- | --------- | ------ |
| apiKey    | Api Key               | query        | true     | string    |        |
| blockHash | Block tx hash         | query        | true     | string    |        |

**Response Status**:

| Status | Illustrate   | schema             |
| ------ | ------------ | ------------------ |
| 200    | OK           | JsonResult«Blocks» |
| 401    | Unauthorized |                    |
| 403    | Forbidden    |                    |
| 404    | Not Found    |                    |

**Response parameters**:

| Parameter         | Parameter Description | Types          | schema |
| ----------------- | --------------------- | -------------- | ------ |
| code              | integer(int32)        | integer(int32) |        |
| data              | Blocks                | Blocks         |        |
|   baseFeePerGas   | integer(int64)        |                |        |
|   blockHash       | string                |                |        |
|   consensus       | boolean               |                |        |
|   difficulty      | integer(int64)        |                |        |
|   gasLimit        | integer(int64)        |                |        |
|   gasUsed         | integer(int64)        |                |        |
|   isEmpty         | boolean               |                |        |
|   minerHashHex    | string                |                |        |
|   nonceHex        | string                |                |        |
|   number          | integer(int64)        |                |        |
|   parentHashHex   | string                |                |        |
|   refetchNeeded   | boolean               |                |        |
|   size            | integer(int32)        |                |        |
|   totalDifficulty | integer(int64)        |                |        |
| msg               | string                |                |        |
| success           | boolean               |                |        |

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

### Query transaction block information based on block hash

**uri**:`/api/block/getBlockByHash`

**Request Method**:`POST`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter | Parameter Description | Request type | Required | Data type | schema |
| --------- | --------------------- | ------------ | -------- | --------- | ------ |
| apiKey    | Api Key               | query        | true     | string    |        |
| blockHash | Block tx hash         | query        | true     | string    |        |

**Response Status**:

| Status | Illustrate   | schema             |
| ------ | ------------ | ------------------ |
| 200    | OK           | JsonResult«Blocks» |
| 201    | Created      |                    |
| 401    | Unauthorized |                    |
| 403    | Forbidden    |                    |
| 404    | Not Found    |                    |

**Response parameters**:

| Parameter         | Parameter Description | Types          | schema |
| ----------------- | --------------------- | -------------- | ------ |
| code              | integer(int32)        | integer(int32) |        |
| data              | Blocks                | Blocks         |        |
|   baseFeePerGas   | integer(int64)        |                |        |
|   blockHash       | string                |                |        |
|   consensus       | boolean               |                |        |
|   difficulty      | integer(int64)        |                |        |
|   gasLimit        | integer(int64)        |                |        |
|   gasUsed         | integer(int64)        |                |        |
|   isEmpty         | boolean               |                |        |
|   minerHashHex    | string                |                |        |
|   nonceHex        | string                |                |        |
|   number          | integer(int64)        |                |        |
|   parentHashHex   | string                |                |        |
|   refetchNeeded   | boolean               |                |        |
|   size            | integer(int32)        |                |        |
|   totalDifficulty | integer(int64)        |                |        |
| msg               | string                |                |        |
| success           | boolean               |                |        |

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

## Transaction information interface

### Query transaction information based on txhash

**uri**:`/api/transaction/txByHash`

**Request Method**:`GET`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter | Parameter Description | Request type | Required | Data type | schema |
| --------- | --------------------- | ------------ | -------- | --------- | ------ |
| apiKey    | Api Key               | query        | true     | string    |        |
| hash      | Tx hash               | query        | true     | string    |        |

**Response Status**:

| Status | Illustrate   | schema                   |
| ------ | ------------ | ------------------------ |
| 200    | OK           | JsonResult«Transactions» |
| 401    | Unauthorized |                          |
| 403    | Forbidden    |                          |
| 404    | Not Found    |                          |

**Response parameters**:

| Parameter                      | Parameter Description | Types          | schema |
| ------------------------------ | --------------------- | -------------- | ------ |
| code                           | integer(int32)        | integer(int32) |        |
| data                           | Transactions          | Transactions   |        |
|   blockHashHex                 | string                |                |        |
|   blockNumber                  | integer(int32)        |                |        |
|   createdContractAddress       | string                |                |        |
|   createdContractCodeIndexedAt | string(date-time)     |                |        |
|   cumulativeGasUsed            | integer(int64)        |                |        |
|   earliestProcessingStart      | string(date-time)     |                |        |
|   error                        | string                |                |        |
|   fromAddress                  | string                |                |        |
|   gas                          | integer(int64)        |                |        |
|   gasPrice                     | integer(int64)        |                |        |
|   gasUsed                      | integer(int64)        |                |        |
|   hasErrorInInternalTxs        | boolean               |                |        |
|   index                        | integer(int32)        |                |        |
|   inputHex                     | string                |                |        |
|   maxFeePerGas                 | integer(int64)        |                |        |
|   maxPriorityFeePerGas         | integer(int64)        |                |        |
|   nonce                        | integer(int32)        |                |        |
|   oldBlockHashHex              | string                |                |        |
|   r                            | string                |                |        |
|   revertReason                 | string                |                |        |
|   s                            | string                |                |        |
|   status                       | integer(int32)        |                |        |
|   toAddress                    | string                |                |        |
|   transactionsHash             | string                |                |        |
|   type                         | integer(int32)        |                |        |
|   v                            | string                |                |        |
|   value                        | number(bigdecimal)    |                |        |
| msg                            | string                |                |        |
| success                        | boolean               |                |        |

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

### Query transaction information based on txhash

**uri**:`/api/transaction/txByHash`

**Request Method**:`POST`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter | Parameter Description | Request type | Required | Data type | schema |
| --------- | --------------------- | ------------ | -------- | --------- | ------ |
| apiKey    | Api Key               | query        | true     | string    |        |
| hash      | Tx hash               | query        | true     | string    |        |

**Response Status**:

| Status | Illustrate   | schema                   |
| ------ | ------------ | ------------------------ |
| 200    | OK           | JsonResult«Transactions» |
| 201    | Created      |                          |
| 401    | Unauthorized |                          |
| 403    | Forbidden    |                          |
| 404    | Not Found    |                          |

**Response parameters**:

| Parameter                      | Parameter Description | Types          | schema |
| ------------------------------ | --------------------- | -------------- | ------ |
| code                           | integer(int32)        | integer(int32) |        |
| data                           | Transactions          | Transactions   |        |
|   blockHashHex                 | string                |                |        |
|   blockNumber                  | integer(int32)        |                |        |
|   createdContractAddress       | string                |                |        |
|   createdContractCodeIndexedAt | string(date-time)     |                |        |
|   cumulativeGasUsed            | integer(int64)        |                |        |
|   earliestProcessingStart      | string(date-time)     |                |        |
|   error                        | string                |                |        |
|   fromAddress                  | string                |                |        |
|   gas                          | integer(int64)        |                |        |
|   gasPrice                     | integer(int64)        |                |        |
|   gasUsed                      | integer(int64)        |                |        |
|   hasErrorInInternalTxs        | boolean               |                |        |
|   index                        | integer(int32)        |                |        |
|   inputHex                     | string                |                |        |
|   maxFeePerGas                 | integer(int64)        |                |        |
|   maxPriorityFeePerGas         | integer(int64)        |                |        |
|   nonce                        | integer(int32)        |                |        |
|   oldBlockHashHex              | string                |                |        |
|   r                            | string                |                |        |
|   revertReason                 | string                |                |        |
|   s                            | string                |                |        |
|   status                       | integer(int32)        |                |        |
|   toAddress                    | string                |                |        |
|   transactionsHash             | string                |                |        |
|   type                         | integer(int32)        |                |        |
|   v                            | string                |                |        |
|   value                        | number(bigdecimal)    |                |        |
| msg                            | string                |                |        |
| success                        | boolean               |                |        |

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

### Query transaction information based on txhash

**uri**:`/api/transaction/txInternalByHash`

**Request Method**:`GET`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter | Parameter Description | Request type | Required | Data type | schema |
| --------- | --------------------- | ------------ | -------- | --------- | ------ |
| apiKey    | Api Key               | query        | true     | string    |        |
| hash      | Tx hash               | query        | true     | string    |        |

**Response Status**:

| Status | Illustrate   | schema                           |
| ------ | ------------ | -------------------------------- |
| 200    | OK           | JsonResult«InternalTransactions» |
| 401    | Unauthorized |                                  |
| 403    | Forbidden    |                                  |
| 404    | Not Found    |                                  |

**Response parameters**:

| Parameter                | Parameter Description | Types                | schema |
| ------------------------ | --------------------- | -------------------- | ------ |
| code                     | integer(int32)        | integer(int32)       |        |
| data                     | InternalTransactions  | InternalTransactions |        |
|   blockHashHex           | string                |                      |        |
|   blockIndex             | integer(int32)        |                      |        |
|   blockNumber            | integer(int32)        |                      |        |
|   callType               | string                |                      |        |
|   createdContractAddress | string                |                      |        |
|   createdContractCodeHex | string                |                      |        |
|   error                  | string                |                      |        |
|   fromAddress            | string                |                      |        |
|   gas                    | integer(int64)        |                      |        |
|   gasUsed                | integer(int64)        |                      |        |
|   index                  | integer(int32)        |                      |        |
|   initHex                | string                |                      |        |
|   inputHex               | string                |                      |        |
|   insertedAt             | string(date-time)     |                      |        |
|   outputHex              | string                |                      |        |
|   toAddress              | string                |                      |        |
|   transactionHashHex     | string                |                      |        |
|   transactionIndex       | integer(int32)        |                      |        |
|   type                   | string                |                      |        |
|   updatedAt              | string(date-time)     |                      |        |
|   value                  | integer(int64)        |                      |        |
| msg                      | string                |                      |        |
| success                  | boolean               |                      |        |

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

### Query transaction information based on txhash

**uri**:`/api/transaction/txInternalByHash`

**Request Method**:`POST`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter | Parameter Description | Request type | Required | Data type | schema |
| --------- | --------------------- | ------------ | -------- | --------- | ------ |
| apiKey    | Api Key               | query        | true     | string    |        |
| hash      | Tx hash               | query        | true     | string    |        |

**Response Status**:

| Status | Illustrate   | schema                           |
| ------ | ------------ | -------------------------------- |
| 200    | OK           | JsonResult«InternalTransactions» |
| 201    | Created      |                                  |
| 401    | Unauthorized |                                  |
| 403    | Forbidden    |                                  |
| 404    | Not Found    |                                  |

**Response parameters**:

| Parameter                | Parameter Description | Types                | schema |
| ------------------------ | --------------------- | -------------------- | ------ |
| code                     | integer(int32)        | integer(int32)       |        |
| data                     | InternalTransactions  | InternalTransactions |        |
|   blockHashHex           | string                |                      |        |
|   blockIndex             | integer(int32)        |                      |        |
|   blockNumber            | integer(int32)        |                      |        |
|   callType               | string                |                      |        |
|   createdContractAddress | string                |                      |        |
|   createdContractCodeHex | string                |                      |        |
|   error                  | string                |                      |        |
|   fromAddress            | string                |                      |        |
|   gas                    | integer(int64)        |                      |        |
|   gasUsed                | integer(int64)        |                      |        |
|   index                  | integer(int32)        |                      |        |
|   initHex                | string                |                      |        |
|   inputHex               | string                |                      |        |
|   insertedAt             | string(date-time)     |                      |        |
|   outputHex              | string                |                      |        |
|   toAddress              | string                |                      |        |
|   transactionHashHex     | string                |                      |        |
|   transactionIndex       | integer(int32)        |                      |        |
|   type                   | string                |                      |        |
|   updatedAt              | string(date-time)     |                      |        |
|   value                  | integer(int64)        |                      |        |
| msg                      | string                |                      |        |
| success                  | boolean               |                      |        |

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

## User Information Interface

### Query address balance

**uri**:`/api/account/balance`

**Request Method**:`GET`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter | Parameter Description | Request type | Required | Data type | schema |
| --------- | --------------------- | ------------ | -------- | --------- | ------ |
| address   | Wallet address        | query        | true     | string    |        |
| apiKey    | Api Key               | query        | true     | string    |        |

**Response Status**:

| Status | Illustrate   | schema             |
| ------ | ------------ | ------------------ |
| 200    | OK           | JsonResult«string» |
| 401    | Unauthorized |                    |
| 403    | Forbidden    |                    |
| 404    | Not Found    |                    |

**Response parameters**:

| Parameter | Parameter Description | Types          | schema |
| --------- | --------------------- | -------------- | ------ |
| code      | integer(int32)        | integer(int32) |        |
| data      | string                |                |        |
| msg       | string                |                |        |
| success   | boolean               |                |        |

**Response Example**:

```javascript
{
	"code": 0,
	"data": "",
	"msg": "",
	"success": true
}
```

### Query address balance

**uri**:`/api/account/balance`

**Request Method**:`POST`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter | Parameter Description | Request type | Required | Data type | schema |
| --------- | --------------------- | ------------ | -------- | --------- | ------ |
| address   | Wallet address        | query        | true     | string    |        |
| apiKey    | Api Key               | query        | true     | string    |        |

**Response Status**:

| Status | Illustrate   | schema             |
| ------ | ------------ | ------------------ |
| 200    | OK           | JsonResult«string» |
| 201    | Created      |                    |
| 401    | Unauthorized |                    |
| 403    | Forbidden    |                    |
| 404    | Not Found    |                    |

**Response parameters**:

| Parameter | Parameter Description | Types          | schema |
| --------- | --------------------- | -------------- | ------ |
| code      | integer(int32)        | integer(int32) |        |
| data      | string                |                |        |
| msg       | string                |                |        |
| success   | boolean               |                |        |

**Response Example**:

```javascript
{
	"code": 0,
	"data": "",
	"msg": "",
	"success": true
}
```

### Query the number of tokens owned by the address

**uri**:`/api/account/tokenBalance`

**Request Method**:`GET`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter       | Parameter Description  | Request type | Required | Data type | schema |
| --------------- | ---------------------- | ------------ | -------- | --------- | ------ |
| address         | Wallet address         | query        | true     | string    |        |
| apiKey          | Api Key                | query        | true     | string    |        |
| contractAddress | Token contract address | query        | false    | string    |        |

**Response Status**:

| Status | Illustrate   | schema                         |
| ------ | ------------ | ------------------------------ |
| 200    | OK           | JsonResult«List«TokenBalance»» |
| 401    | Unauthorized |                                |
| 403    | Forbidden    |                                |
| 404    | Not Found    |                                |

**Response parameters**:

| Parameter         | Parameter Description | Types          | schema |
| ----------------- | --------------------- | -------------- | ------ |
| code              | integer(int32)        | integer(int32) |        |
| data              | array                 | TokenBalance   |        |
|   contractAddress | string                |                |        |
|   creator         | string                |                |        |
|   decimals        | string                |                |        |
|   name            | string                |                |        |
|   owner           | string                |                |        |
|   symbol          | string                |                |        |
|   tokens          | array                 | TokenIdDto     |        |
|     balance       | number                |                |        |
|     tokenId       | string                |                |        |
|   type            | string                |                |        |
| msg               | string                |                |        |
| success           | boolean               |                |        |

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

### Query the number of tokens owned by the address

**uri**:`/api/account/tokenBalance`

**Request Method**:`POST`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter       | Parameter Description  | Request type | Required | Data type | schema |
| --------------- | ---------------------- | ------------ | -------- | --------- | ------ |
| address         | Wallet address         | query        | true     | string    |        |
| apiKey          | Api Key                | query        | true     | string    |        |
| contractAddress | Token contract address | query        | false    | string    |        |

**Response Status**:

| Status | Illustrate   | schema                         |
| ------ | ------------ | ------------------------------ |
| 200    | OK           | JsonResult«List«TokenBalance»» |
| 201    | Created      |                                |
| 401    | Unauthorized |                                |
| 403    | Forbidden    |                                |
| 404    | Not Found    |                                |

**Response parameters**:

| Parameter         | Parameter Description | Types          | schema |
| ----------------- | --------------------- | -------------- | ------ |
| code              | integer(int32)        | integer(int32) |        |
| data              | array                 | TokenBalance   |        |
|   contractAddress | string                |                |        |
|   creator         | string                |                |        |
|   decimals        | string                |                |        |
|   name            | string                |                |        |
|   owner           | string                |                |        |
|   symbol          | string                |                |        |
|   tokens          | array                 | TokenIdDto     |        |
|     balance       | number                |                |        |
|     tokenId       | string                |                |        |
|   type            | string                |                |        |
| msg               | string                |                |        |
| success           | boolean               |                |        |

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

### The total number of tokens owned by the query address

**uri**:`/api/account/tokenList`

**Request Method**:`GET`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter | Parameter Description | Request type | Required | Data type | schema |
| --------- | --------------------- | ------------ | -------- | --------- | ------ |
| address   | Wallet address        | query        | true     | string    |        |
| apiKey    | Api Key               | query        | true     | string    |        |

**Response Status**:

| Status | Illustrate   | schema                         |
| ------ | ------------ | ------------------------------ |
| 200    | OK           | JsonResult«List«TokenListDto»» |
| 401    | Unauthorized |                                |
| 403    | Forbidden    |                                |
| 404    | Not Found    |                                |

**Response parameters**:

| Parameter         | Parameter Description | Types          | schema |
| ----------------- | --------------------- | -------------- | ------ |
| code              | integer(int32)        | integer(int32) |        |
| data              | array                 | TokenListDto   |        |
|   balance         | number(bigdecimal)    |                |        |
|   contractAddress | string                |                |        |
|   creator         | string                |                |        |
|   decimals        | string                |                |        |
|   name            | string                |                |        |
|   owner           | string                |                |        |
|   symbol          | string                |                |        |
|   type            | string                |                |        |
| msg               | string                |                |        |
| success           | boolean               |                |        |

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

### The total number of tokens owned by the query address

**uri**:`/api/account/tokenList`

**Request Method**:`POST`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter | Parameter Description | Request type | Required | Data type | schema |
| --------- | --------------------- | ------------ | -------- | --------- | ------ |
| address   | Wallet address        | query        | true     | string    |        |
| apiKey    | Api Key               | query        | true     | string    |        |

**Response Status**:

| Status | Illustrate   | schema                         |
| ------ | ------------ | ------------------------------ |
| 200    | OK           | JsonResult«List«TokenListDto»» |
| 201    | Created      |                                |
| 401    | Unauthorized |                                |
| 403    | Forbidden    |                                |
| 404    | Not Found    |                                |

**Response parameters**:

| Parameter         | Parameter Description | Types          | schema |
| ----------------- | --------------------- | -------------- | ------ |
| code              | integer(int32)        | integer(int32) |        |
| data              | array                 | TokenListDto   |        |
|   balance         | number(bigdecimal)    |                |        |
|   contractAddress | string                |                |        |
|   creator         | string                |                |        |
|   decimals        | string                |                |        |
|   name            | string                |                |        |
|   owner           | string                |                |        |
|   symbol          | string                |                |        |
|   type            | string                |                |        |
| msg               | string                |                |        |
| success           | boolean               |                |        |

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

### Query token transaction information based on wallet address

**uri**:`/api/account/tokenTxList`

**Request Method**:`GET`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter            | Parameter Description      | Request type | Required | Data type      | schema |
| -------------------- | -------------------------- | ------------ | -------- | -------------- | ------ |
| address              | Wallet address             | query        | true     | string         |        |
| apiKey               | Api Key                    | query        | true     | string         |        |
| tokenContractAddress | Token contract address     | query        | true     | string         |        |
| pageNumber           | page number                | query        | false    | integer(int32) |        |
| pageSize             | Number of entries per page | query        | false    | integer(int32) |        |
| sort                 | Sort Rule (desc            | asc)         | query    | false          | string |

**Response Status**:

| Status | Illustrate   | schema                                |
| ------ | ------------ | ------------------------------------- |
| 200    | OK           | JsonResult«PageQuery«TokenTransfers»» |
| 401    | Unauthorized |                                       |
| 403    | Forbidden    |                                       |
| 404    | Not Found    |                                       |

**Response parameters**:

| Parameter                | Parameter Description     | Types                     | schema |
| ------------------------ | ------------------------- | ------------------------- | ------ |
| code                     | integer(int32)            | integer(int32)            |        |
| data                     | PageQuery«TokenTransfers» | PageQuery«TokenTransfers» |        |
|   firstPage              | boolean                   |                           |        |
|   lastPage               | boolean                   |                           |        |
|   list                   | array                     | TokenTransfers            |        |
|     amount               | number                    |                           |        |
|     blockHashHex         | string                    |                           |        |
|     blockNumber          | integer                   |                           |        |
|     fromAddress          | string                    |                           |        |
|     logIndex             | integer                   |                           |        |
|     toAddress            | string                    |                           |        |
|     tokenContractAddress | string                    |                           |        |
|     tokenId              | string                    |                           |        |
|     transactionHashHex   | string                    |                           |        |
|   orderBy                | string                    |                           |        |
|   pageNumber             | integer(int64)            |                           |        |
|   pageSize               | integer(int64)            |                           |        |
|   paras                  | object                    |                           |        |
|   totalPage              | integer(int64)            |                           |        |
|   totalRow               | integer(int64)            |                           |        |
| msg                      | string                    |                           |        |
| success                  | boolean                   |                           |        |

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

### Query token transaction information based on wallet address

**uri**:`/api/account/tokenTxList`

**Request Method**:`POST`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter            | Parameter Description      | Request type | Required | Data type      | schema |
| -------------------- | -------------------------- | ------------ | -------- | -------------- | ------ |
| address              | Wallet address             | query        | true     | string         |        |
| apiKey               | Api Key                    | query        | true     | string         |        |
| tokenContractAddress | Token contract address     | query        | true     | string         |        |
| pageNumber           | page number                | query        | false    | integer(int32) |        |
| pageSize             | Number of entries per page | query        | false    | integer(int32) |        |
| sort                 | Sort Rule (desc            | asc)         | query    | false          | string |

**Response Status**:

| Status | Illustrate   | schema                                |
| ------ | ------------ | ------------------------------------- |
| 200    | OK           | JsonResult«PageQuery«TokenTransfers»» |
| 201    | Created      |                                       |
| 401    | Unauthorized |                                       |
| 403    | Forbidden    |                                       |
| 404    | Not Found    |                                       |

**Response parameters**:

| Parameter                | Parameter Description     | Types                     | schema |
| ------------------------ | ------------------------- | ------------------------- | ------ |
| code                     | integer(int32)            | integer(int32)            |        |
| data                     | PageQuery«TokenTransfers» | PageQuery«TokenTransfers» |        |
|   firstPage              | boolean                   |                           |        |
|   lastPage               | boolean                   |                           |        |
|   list                   | array                     | TokenTransfers            |        |
|     amount               | number                    |                           |        |
|     blockHashHex         | string                    |                           |        |
|     blockNumber          | integer                   |                           |        |
|     fromAddress          | string                    |                           |        |
|     logIndex             | integer                   |                           |        |
|     toAddress            | string                    |                           |        |
|     tokenContractAddress | string                    |                           |        |
|     tokenId              | string                    |                           |        |
|     transactionHashHex   | string                    |                           |        |
|   orderBy                | string                    |                           |        |
|   pageNumber             | integer(int64)            |                           |        |
|   pageSize               | integer(int64)            |                           |        |
|   paras                  | object                    |                           |        |
|   totalPage              | integer(int64)            |                           |        |
|   totalRow               | integer(int64)            |                           |        |
| msg                      | string                    |                           |        |
| success                  | boolean                   |                           |        |

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

### Query transaction information based on wallet address

**uri**:`/api/account/txList`

**Request Method**:`GET`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter  | Parameter Description      | Request type | Required | Data type      | schema |
| ---------- | -------------------------- | ------------ | -------- | -------------- | ------ |
| address    | Wallet address             | query        | true     | string         |        |
| apiKey     | Api Key                    | query        | true     | string         |        |
| pageNumber | page number                | query        | false    | integer(int32) |        |
| pageSize   | Number of entries per page | query        | false    | integer(int32) |        |
| sort       | Sort Rule (desc            | asc)         | query    | false          | string |

**Response Status**:

| Status | Illustrate   | schema                              |
| ------ | ------------ | ----------------------------------- |
| 200    | OK           | JsonResult«PageQuery«Transactions»» |
| 401    | Unauthorized |                                     |
| 403    | Forbidden    |                                     |
| 404    | Not Found    |                                     |

**Response parameters**:

| Parameter                        | Parameter Description   | Types                   | schema |
| -------------------------------- | ----------------------- | ----------------------- | ------ |
| code                             | integer(int32)          | integer(int32)          |        |
| data                             | PageQuery«Transactions» | PageQuery«Transactions» |        |
|   firstPage                      | boolean                 |                         |        |
|   lastPage                       | boolean                 |                         |        |
|   list                           | array                   | Transactions            |        |
|     blockHashHex                 | string                  |                         |        |
|     blockNumber                  | integer                 |                         |        |
|     createdContractAddress       | string                  |                         |        |
|     createdContractCodeIndexedAt | string                  |                         |        |
|     cumulativeGasUsed            | integer                 |                         |        |
|     earliestProcessingStart      | string                  |                         |        |
|     error                        | string                  |                         |        |
|     fromAddress                  | string                  |                         |        |
|     gas                          | integer                 |                         |        |
|     gasPrice                     | integer                 |                         |        |
|     gasUsed                      | integer                 |                         |        |
|     hasErrorInInternalTxs        | boolean                 |                         |        |
|     index                        | integer                 |                         |        |
|     inputHex                     | string                  |                         |        |
|     maxFeePerGas                 | integer                 |                         |        |
|     maxPriorityFeePerGas         | integer                 |                         |        |
|     nonce                        | integer                 |                         |        |
|     oldBlockHashHex              | string                  |                         |        |
|     r                            | string                  |                         |        |
|     revertReason                 | string                  |                         |        |
|     s                            | string                  |                         |        |
|     status                       | integer                 |                         |        |
|     toAddress                    | string                  |                         |        |
|     transactionsHash             | string                  |                         |        |
|     type                         | integer                 |                         |        |
|     v                            | string                  |                         |        |
|     value                        | number                  |                         |        |
|   orderBy                        | string                  |                         |        |
|   pageNumber                     | integer(int64)          |                         |        |
|   pageSize                       | integer(int64)          |                         |        |
|   paras                          | object                  |                         |        |
|   totalPage                      | integer(int64)          |                         |        |
|   totalRow                       | integer(int64)          |                         |        |
| msg                              | string                  |                         |        |
| success                          | boolean                 |                         |        |

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

### Query transaction information based on wallet address

**uri**:`/api/account/txList`

**Request Method**:`POST`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter  | Parameter Description      | Request type | Required | Data type      | schema |
| ---------- | -------------------------- | ------------ | -------- | -------------- | ------ |
| address    | Wallet address             | query        | true     | string         |        |
| apiKey     | Api Key                    | query        | true     | string         |        |
| pageNumber | page number                | query        | false    | integer(int32) |        |
| pageSize   | Number of entries per page | query        | false    | integer(int32) |        |
| sort       | Sort Rule (desc            | asc)         | query    | false          | string |

**Response Status**:

| Status | Illustrate   | schema                              |
| ------ | ------------ | ----------------------------------- |
| 200    | OK           | JsonResult«PageQuery«Transactions»» |
| 201    | Created      |                                     |
| 401    | Unauthorized |                                     |
| 403    | Forbidden    |                                     |
| 404    | Not Found    |                                     |

**Response parameters**:

| Parameter                        | Parameter Description   | Types                   | schema |
| -------------------------------- | ----------------------- | ----------------------- | ------ |
| code                             | integer(int32)          | integer(int32)          |        |
| data                             | PageQuery«Transactions» | PageQuery«Transactions» |        |
|   firstPage                      | boolean                 |                         |        |
|   lastPage                       | boolean                 |                         |        |
|   list                           | array                   | Transactions            |        |
|     blockHashHex                 | string                  |                         |        |
|     blockNumber                  | integer                 |                         |        |
|     createdContractAddress       | string                  |                         |        |
|     createdContractCodeIndexedAt | string                  |                         |        |
|     cumulativeGasUsed            | integer                 |                         |        |
|     earliestProcessingStart      | string                  |                         |        |
|     error                        | string                  |                         |        |
|     fromAddress                  | string                  |                         |        |
|     gas                          | integer                 |                         |        |
|     gasPrice                     | integer                 |                         |        |
|     gasUsed                      | integer                 |                         |        |
|     hasErrorInInternalTxs        | boolean                 |                         |        |
|     index                        | integer                 |                         |        |
|     inputHex                     | string                  |                         |        |
|     maxFeePerGas                 | integer                 |                         |        |
|     maxPriorityFeePerGas         | integer                 |                         |        |
|     nonce                        | integer                 |                         |        |
|     oldBlockHashHex              | string                  |                         |        |
|     r                            | string                  |                         |        |
|     revertReason                 | string                  |                         |        |
|     s                            | string                  |                         |        |
|     status                       | integer                 |                         |        |
|     toAddress                    | string                  |                         |        |
|     transactionsHash             | string                  |                         |        |
|     type                         | integer                 |                         |        |
|     v                            | string                  |                         |        |
|     value                        | number                  |                         |        |
|   orderBy                        | string                  |                         |        |
|   pageNumber                     | integer(int64)          |                         |        |
|   pageSize                       | integer(int64)          |                         |        |
|   paras                          | object                  |                         |        |
|   totalPage                      | integer(int64)          |                         |        |
|   totalRow                       | integer(int64)          |                         |        |
| msg                              | string                  |                         |        |
| success                          | boolean                 |                         |        |

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

### Query Internal transaction information based on wallet address

**uri**:`/api/account/txListInternal`

**Request Method**:`GET`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter  | Parameter Description      | Request type | Required | Data type      | schema |
| ---------- | -------------------------- | ------------ | -------- | -------------- | ------ |
| address    | Wallet address             | query        | true     | string         |        |
| apiKey     | Api Key                    | query        | true     | string         |        |
| pageNumber | page number                | query        | false    | integer(int32) |        |
| pageSize   | Number of entries per page | query        | false    | integer(int32) |        |
| sort       | Sort Rule (desc            | asc)         | query    | false          | string |

**Response Status**:

| Status | Illustrate   | schema                                      |
| ------ | ------------ | ------------------------------------------- |
| 200    | OK           | JsonResult«PageQuery«InternalTransactions»» |
| 401    | Unauthorized |                                             |
| 403    | Forbidden    |                                             |
| 404    | Not Found    |                                             |

**Response parameters**:

| Parameter                  | Parameter Description           | Types                           | schema |
| -------------------------- | ------------------------------- | ------------------------------- | ------ |
| code                       | integer(int32)                  | integer(int32)                  |        |
| data                       | PageQuery«InternalTransactions» | PageQuery«InternalTransactions» |        |
|   firstPage                | boolean                         |                                 |        |
|   lastPage                 | boolean                         |                                 |        |
|   list                     | array                           | InternalTransactions            |        |
|     blockHashHex           | string                          |                                 |        |
|     blockIndex             | integer                         |                                 |        |
|     blockNumber            | integer                         |                                 |        |
|     callType               | string                          |                                 |        |
|     createdContractAddress | string                          |                                 |        |
|     createdContractCodeHex | string                          |                                 |        |
|     error                  | string                          |                                 |        |
|     fromAddress            | string                          |                                 |        |
|     gas                    | integer                         |                                 |        |
|     gasUsed                | integer                         |                                 |        |
|     index                  | integer                         |                                 |        |
|     initHex                | string                          |                                 |        |
|     inputHex               | string                          |                                 |        |
|     insertedAt             | string                          |                                 |        |
|     outputHex              | string                          |                                 |        |
|     toAddress              | string                          |                                 |        |
|     transactionHashHex     | string                          |                                 |        |
|     transactionIndex       | integer                         |                                 |        |
|     type                   | string                          |                                 |        |
|     updatedAt              | string                          |                                 |        |
|     value                  | integer                         |                                 |        |
|   orderBy                  | string                          |                                 |        |
|   pageNumber               | integer(int64)                  |                                 |        |
|   pageSize                 | integer(int64)                  |                                 |        |
|   paras                    | object                          |                                 |        |
|   totalPage                | integer(int64)                  |                                 |        |
|   totalRow                 | integer(int64)                  |                                 |        |
| msg                        | string                          |                                 |        |
| success                    | boolean                         |                                 |        |

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

### Query Internal transaction information based on wallet address

**uri**:`/api/account/txListInternal`

**Request Method**:`POST`

**Request Data Type**:`application/x-www-form-urlencoded`

**Response Data Type**:`*/*`

**Request parameters**:

| Parameter  | Parameter Description      | Request type | Required | Data type      | schema |
| ---------- | -------------------------- | ------------ | -------- | -------------- | ------ |
| address    | Wallet address             | query        | true     | string         |        |
| apiKey     | Api Key                    | query        | true     | string         |        |
| pageNumber | page number                | query        | false    | integer(int32) |        |
| pageSize   | Number of entries per page | query        | false    | integer(int32) |        |
| sort       | Sort Rule (desc            | asc)         | query    | false          | string |

**Response Status**:

| Status | Illustrate   | schema                                      |
| ------ | ------------ | ------------------------------------------- |
| 200    | OK           | JsonResult«PageQuery«InternalTransactions»» |
| 201    | Created      |                                             |
| 401    | Unauthorized |                                             |
| 403    | Forbidden    |                                             |
| 404    | Not Found    |                                             |

**Response parameters**:

| Parameter                  | Parameter Description           | Types                           | schema |
| -------------------------- | ------------------------------- | ------------------------------- | ------ |
| code                       | integer(int32)                  | integer(int32)                  |        |
| data                       | PageQuery«InternalTransactions» | PageQuery«InternalTransactions» |        |
|   firstPage                | boolean                         |                                 |        |
|   lastPage                 | boolean                         |                                 |        |
|   list                     | array                           | InternalTransactions            |        |
|     blockHashHex           | string                          |                                 |        |
|     blockIndex             | integer                         |                                 |        |
|     blockNumber            | integer                         |                                 |        |
|     callType               | string                          |                                 |        |
|     createdContractAddress | string                          |                                 |        |
|     createdContractCodeHex | string                          |                                 |        |
|     error                  | string                          |                                 |        |
|     fromAddress            | string                          |                                 |        |
|     gas                    | integer                         |                                 |        |
|     gasUsed                | integer                         |                                 |        |
|     index                  | integer                         |                                 |        |
|     initHex                | string                          |                                 |        |
|     inputHex               | string                          |                                 |        |
|     insertedAt             | string                          |                                 |        |
|     outputHex              | string                          |                                 |        |
|     toAddress              | string                          |                                 |        |
|     transactionHashHex     | string                          |                                 |        |
|     transactionIndex       | integer                         |                                 |        |
|     type                   | string                          |                                 |        |
|     updatedAt              | string                          |                                 |        |
|     value                  | integer                         |                                 |        |
|   orderBy                  | string                          |                                 |        |
|   pageNumber               | integer(int64)                  |                                 |        |
|   pageSize                 | integer(int64)                  |                                 |        |
|   paras                    | object                          |                                 |        |
|   totalPage                | integer(int64)                  |                                 |        |
|   totalRow                 | integer(int64)                  |                                 |        |
| msg                        | string                          |                                 |        |
| success                    | boolean                         |                                 |        |

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
