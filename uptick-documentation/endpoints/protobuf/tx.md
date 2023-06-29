
## cosmos/tx/signing/v1beta1/signing.proto

### SignatureDescriptor

SignatureDescriptor is a convenience type which represents the full data for a signature including the public key of the signer, signing modes and the signature itself. It is primarily used for coordinating signatures between clients.

| Field        | Type                                                                                         | Label | Description                                                                                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `public_key` | google.protobuf.Any                                     |       | public_key is the public key of the signer                                                                                                                    |
| `data`       | [SignatureDescriptor.Data](tx.md#cosmos.tx.signing.v1beta1.SignatureDescriptor.Data) |       |                                                                                                                                                                |
| `sequence`   | [uint64](value.md#uint64)                                                               |       | sequence is the sequence of the account, which describes the number of committed transactions signed by a given address. It is used to prevent replay attacks. |

### SignatureDescriptor.Data

Data represents signature data

| Field    | Type                                                                                                       | Label | Description                        |
| -------- | ---------------------------------------------------------------------------------------------------------- | ----- | ---------------------------------- |
| `single` | [SignatureDescriptor.Data.Single](tx.md#cosmos.tx.signing.v1beta1.SignatureDescriptor.Data.Single) |       | single represents a single signer  |
| `multi`  | [SignatureDescriptor.Data.Multi](tx.md#cosmos.tx.signing.v1beta1.SignatureDescriptor.Data.Multi)   |       | multi represents a multisig signer |

### SignatureDescriptor.Data.Multi

Multi is the signature data for a multisig public key

| Field        | Type                                                                                                           | Label    | Description                                                   |
| ------------ | -------------------------------------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------- |
| `bitarray`   | [cosmos.crypto.multisig.v1beta1.CompactBitArray](crypto.md#cosmos.crypto.multisig.v1beta1.CompactBitArray) |          | bitarray specifies which keys within the multisig are signing |
| `signatures` | [SignatureDescriptor.Data](tx.md#cosmos.tx.signing.v1beta1.SignatureDescriptor.Data)                   | repeated | signatures is the signatures of the multi-signature           |

### SignatureDescriptor.Data.Single

Single is the signature data for a single signer

| Field       | Type                                                         | Label | Description                                   |
| ----------- | ------------------------------------------------------------ | ----- | --------------------------------------------- |
| `mode`      | [SignMode](tx.md#cosmos.tx.signing.v1beta1.SignMode) |       | mode is the signing mode of the single signer |
| `signature` | [bytes](value.md#bytes)                                 |       | signature is the raw signature bytes          |

### SignatureDescriptors

SignatureDescriptors wraps multiple SignatureDescriptor's.

| Field        | Type                                                                               | Label    | Description                              |
| ------------ | ---------------------------------------------------------------------------------- | -------- | ---------------------------------------- |
| `signatures` | [SignatureDescriptor](tx.md#cosmos.tx.signing.v1beta1.SignatureDescriptor) | repeated | signatures are the signature descriptors |

### SignMode

SignMode represents a signing mode with its own security guarantees.

| Name                            | Number | Description                                                                                                                                                          |
| ------------------------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SIGN_MODE_UNSPECIFIED         | 0      | SIGN_MODE_UNSPECIFIED specifies an unknown signing mode and will be rejected                                                                                       |
| SIGN_MODE_DIRECT              | 1      | SIGN_MODE_DIRECT specifies a signing mode which uses SignDoc and is verified with raw bytes from Tx                                                                |
| SIGN_MODE_TEXTUAL             | 2      | SIGN_MODE_TEXTUAL is a future signing mode that will verify some human-readable textual representation on top of the binary representation from SIGN_MODE_DIRECT |
| SIGN_MODE_LEGACY_AMINO_JSON | 127    | SIGN_MODE_LEGACY_AMINO_JSON is a backwards compatibility mode which uses Amino JSON and will be removed in the future                                            |



## cosmos/tx/v1beta1/tx.proto

### AuthInfo

AuthInfo describes the fee and signer modes that are used to sign a transaction.

| Field          | Type                                                     | Label    | Description                                                                                                                                                                                                                                                                        |
| -------------- | -------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `signer_infos` | [SignerInfo](tx.md#cosmos.tx.v1beta1.SignerInfo) | repeated | signer_infos defines the signing modes for the required signers. The number and order of elements must match the required signers from TxBody's messages. The first element is the primary signer and the one which pays the fee.                                                 |
| `fee`          | [Fee](tx.md#cosmos.tx.v1beta1.Fee)               |          | Fee is the fee and gas limit for the transaction. The first signer is the primary signer and the one which pays the fee. The fee can be calculated based on the cost of evaluating the body and doing signature verification of the signers. This can be estimated via simulation. |

### Fee

Fee includes the amount of coins paid in fees and the maximum gas to be used by the transaction. The ratio yields an effective "gasprice", which must be above some miminum to be accepted into the mempool.

| Field       | Type                                                               | Label    | Description                                                                                                                                                                                                                                                                             |
| ----------- | ------------------------------------------------------------------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `amount`    | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated | amount is the amount of coins to be paid as a fee                                                                                                                                                                                                                                       |
| `gas_limit` | [uint64](value.md#uint64)                                     |          | gas_limit is the maximum gas that can be used in transaction processing before an out of gas error occurs                                                                                                                                                                              |
| `payer`     | [string](value.md#string)                                     |          | if unset, the first signer is responsible for paying the fees. If set, the specified account must pay the fees. the payer must be a tx signer (and thus have signed this field in AuthInfo). setting this field does _not_ change the ordering of required signers for the transaction. |
| `granter`   | [string](value.md#string)                                     |          | if set, the fee payer (either the first signer or the value of the payer field) requests that a fee grant be used to pay fees instead of the fee payer's own balance. If an appropriate fee grant does not exist or the chain does not support fee grants, this will fail               |

### ModeInfo

ModeInfo describes the signing mode of a single or nested multisig signer.

| Field    | Type                                                               | Label | Description                               |
| -------- | ------------------------------------------------------------------ | ----- | ----------------------------------------- |
| `single` | [ModeInfo.Single](tx.md#cosmos.tx.v1beta1.ModeInfo.Single) |       | single represents a single signer         |
| `multi`  | [ModeInfo.Multi](tx.md#cosmos.tx.v1beta1.ModeInfo.Multi)   |       | multi represents a nested multisig signer |

### ModeInfo.Multi

Multi is the mode info for a multisig public key

| Field        | Type                                                                                                           | Label    | Description                                                                                                           |
| ------------ | -------------------------------------------------------------------------------------------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------- |
| `bitarray`   | [cosmos.crypto.multisig.v1beta1.CompactBitArray](crypto.md#cosmos.crypto.multisig.v1beta1.CompactBitArray) |          | bitarray specifies which keys within the multisig are signing                                                         |
| `mode_infos` | [ModeInfo](tx.md#cosmos.tx.v1beta1.ModeInfo)                                                           | repeated | mode_infos is the corresponding modes of the signers of the multisig which could include nested multisig public keys |

### ModeInfo.Single

Single is the mode info for a single signer. It is structured as a message to allow for additional fields such as locale for SIGN_MODE_TEXTUAL in the future

| Field  | Type                                                                                   | Label | Description                                   |
| ------ | -------------------------------------------------------------------------------------- | ----- | --------------------------------------------- |
| `mode` | [cosmos.tx.signing.v1beta1.SignMode](tx.md#cosmos.tx.signing.v1beta1.SignMode) |       | mode is the signing mode of the single signer |

### SignDoc

SignDoc is the type used for generating sign bytes for SIGN_MODE_DIRECT.

| Field             | Type                           | Label | Description                                                                                                                                               |
| ----------------- | ------------------------------ | ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `body_bytes`      | [bytes](value.md#bytes)   |       | body_bytes is protobuf serialization of a TxBody that matches the representation in TxRaw.                                                               |
| `auth_info_bytes` | [bytes](value.md#bytes)   |       | auth_info_bytes is a protobuf serialization of an AuthInfo that matches the representation in TxRaw.                                                    |
| `chain_id`        | [string](value.md#string) |       | chain_id is the unique identifier of the chain this transaction targets. It prevents signed transactions from being used on another chain by an attacker |
| `account_number`  | [uint64](value.md#uint64) |       | account_number is the account number of the account in state                                                                                             |

### SignerInfo

SignerInfo describes the public key and signing mode of a single top-level signer.

| Field        | Type                                                     | Label | Description                                                                                                                                                                                                     |
| ------------ | -------------------------------------------------------- | ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `public_key` | google.protobuf.Any |       | public_key is the public key of the signer. It is optional for accounts that already exist in state. If unset, the verifier can use the required  signer address for this position and lookup the public key. |
| `mode_info`  | [ModeInfo](tx.md#cosmos.tx.v1beta1.ModeInfo)     |       | mode_info describes the signing mode of the signer and is a nested structure to support nested multisig pubkey's                                                                                               |
| `sequence`   | [uint64](value.md#uint64)                           |       | sequence is the sequence of the account, which describes the number of committed transactions signed by a given address. It is used to prevent replay attacks.                                                  |

### Tx

Tx is the standard type used for broadcasting transactions.

| Field        | Type                                                 | Label    | Description                                                                                                                                                                                   |
| ------------ | ---------------------------------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `body`       | [TxBody](tx.md#cosmos.tx.v1beta1.TxBody)     |          | body is the processable content of the transaction                                                                                                                                            |
| `auth_info`  | [AuthInfo](tx.md#cosmos.tx.v1beta1.AuthInfo) |          | auth_info is the authorization related content of the transaction, specifically signers, signer modes and fee                                                                                |
| `signatures` | [bytes](value.md#bytes)                         | repeated | signatures is a list of signatures that matches the length and order of AuthInfo's signer_infos to allow connecting signature meta information like public key and signing mode by position. |

### TxBody

TxBody is the body of a transaction that all signers sign over.

| Field                            | Type                                                     | Label    | Description                                                                                                                                                                                                                                                                                                                                                                                                                |
| -------------------------------- | -------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `messages`                       | google.protobuf.Any | repeated | messages is a list of messages to be executed. The required signers of those messages define the number and order of elements in AuthInfo's signer_infos and Tx's signatures. Each required signer address is added to the list only the first time it occurs. By convention, the first required signer (usually from the first message) is referred to as the primary signer and pays the fee for the whole transaction. |
| `memo`                           | [string](value.md#string)                           |          | memo is any arbitrary memo to be added to the transaction                                                                                                                                                                                                                                                                                                                                                                  |
| `timeout_height`                 | [uint64](value.md#uint64)                           |          | timeout is the block height after which this transaction will not be processed by the chain                                                                                                                                                                                                                                                                                                                                |
| `extension_options`              | google.protobuf.Any | repeated | extension_options are arbitrary options that can be added by chains when the default options are not sufficient. If any of these are present and can't be handled, the transaction will be rejected                                                                                                                                                                                                                       |
| `non_critical_extension_options` | google.protobuf.Any | repeated | extension_options are arbitrary options that can be added by chains when the default options are not sufficient. If any of these are present and can't be handled, they will be ignored                                                                                                                                                                                                                                   |

### TxRaw

TxRaw is a variant of Tx that pins the signer's exact binary representation of body and auth_info. This is used for signing, broadcasting and verification. The binary `serialize(tx: TxRaw)` is stored in Tendermint and the hash `sha256(serialize(tx: TxRaw))` becomes the "txhash", commonly used as the transaction ID.

| Field             | Type                         | Label    | Description                                                                                                                                                                                   |
| ----------------- | ---------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `body_bytes`      | [bytes](value.md#bytes) |          | body_bytes is a protobuf serialization of a TxBody that matches the representation in SignDoc.                                                                                               |
| `auth_info_bytes` | [bytes](value.md#bytes) |          | auth_info_bytes is a protobuf serialization of an AuthInfo that matches the representation in SignDoc.                                                                                      |
| `signatures`      | [bytes](value.md#bytes) | repeated | signatures is a list of signatures that matches the length and order of AuthInfo's signer_infos to allow connecting signature meta information like public key and signing mode by position. |



## cosmos/tx/v1beta1/service.proto

### BroadcastTxRequest

BroadcastTxRequest is the request type for the Service.BroadcastTxRequest RPC method.

| Field      | Type                                                           | Label | Description                       |
| ---------- | -------------------------------------------------------------- | ----- | --------------------------------- |
| `tx_bytes` | [bytes](value.md#bytes)                                   |       | tx_bytes is the raw transaction. |
| `mode`     | [BroadcastMode](tx.md#cosmos.tx.v1beta1.BroadcastMode) |       |                                   |

### BroadcastTxResponse

BroadcastTxResponse is the response type for the Service.BroadcastTx method.

| Field         | Type                                                                                     | Label | Description                              |
| ------------- | ---------------------------------------------------------------------------------------- | ----- | ---------------------------------------- |
| `tx_response` | [cosmos.base.abci.v1beta1.TxResponse](base.md#cosmos.base.abci.v1beta1.TxResponse) |       | tx_response is the queried TxResponses. |

### GetTxRequest

GetTxRequest is the request type for the Service.GetTx RPC method.

| Field  | Type                           | Label | Description                                            |
| ------ | ------------------------------ | ----- | ------------------------------------------------------ |
| `hash` | [string](value.md#string) |       | hash is the tx hash to query, encoded as a hex string. |

### GetTxResponse

GetTxResponse is the response type for the Service.GetTx method.

| Field         | Type                                                                                     | Label | Description                              |
| ------------- | ---------------------------------------------------------------------------------------- | ----- | ---------------------------------------- |
| `tx`          | [Tx](tx.md#cosmos.tx.v1beta1.Tx)                                                 |       | tx is the queried transaction.           |
| `tx_response` | [cosmos.base.abci.v1beta1.TxResponse](base.md#cosmos.base.abci.v1beta1.TxResponse) |       | tx_response is the queried TxResponses. |

### GetTxsEventRequest

GetTxsEventRequest is the request type for the Service.TxsByEvents RPC method.

| Field        | Type                                                                                         | Label    | Description                                       |
| ------------ | -------------------------------------------------------------------------------------------- | -------- | ------------------------------------------------- |
| `events`     | [string](value.md#string)                                                               | repeated | events is the list of transaction event type.     |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |          | pagination defines an pagination for the request. |
| `order_by`   | [OrderBy](tx.md#cosmos.tx.v1beta1.OrderBy)                                           |          |                                                   |

### GetTxsEventResponse

GetTxsEventResponse is the response type for the Service.TxsByEvents RPC method.

| Field          | Type                                                                                           | Label    | Description                                        |
| -------------- | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `txs`          | [Tx](tx.md#cosmos.tx.v1beta1.Tx)                                                       | repeated | txs is the list of queried transactions.           |
| `tx_responses` | [cosmos.base.abci.v1beta1.TxResponse](base.md#cosmos.base.abci.v1beta1.TxResponse)       | repeated | tx_responses is the list of queried TxResponses.  |
| `pagination`   | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines an pagination for the response. |

### SimulateRequest

SimulateRequest is the request type for the Service.Simulate RPC method.

| Field | Type                                     | Label | Description                        |
| ----- | ---------------------------------------- | ----- | ---------------------------------- |
| `tx`  | [Tx](tx.md#cosmos.tx.v1beta1.Tx) |       | tx is the transaction to simulate. |

### SimulateResponse

SimulateResponse is the response type for the Service.SimulateRPC method.

| Field      | Type                                                                               | Label | Description                                                    |
| ---------- | ---------------------------------------------------------------------------------- | ----- | -------------------------------------------------------------- |
| `gas_info` | [cosmos.base.abci.v1beta1.GasInfo](base.md#cosmos.base.abci.v1beta1.GasInfo) |       | gas_info is the information about gas used in the simulation. |
| `result`   | [cosmos.base.abci.v1beta1.Result](base.md#cosmos.base.abci.v1beta1.Result)   |       | result is the result of the simulation.                        |

### BroadcastMode

BroadcastMode specifies the broadcast mode for the TxService.Broadcast RPC method.

| Name                         | Number | Description                                                                                                         |
| ---------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------- |
| BROADCAST_MODE_UNSPECIFIED | 0      | zero-value for mode ordering                                                                                        |
| BROADCAST_MODE_BLOCK       | 1      | BROADCAST_MODE_BLOCK defines a tx broadcasting mode where the client waits for the tx to be committed in a block. |
| BROADCAST_MODE_SYNC        | 2      | BROADCAST_MODE_SYNC defines a tx broadcasting mode where the client waits for a CheckTx execution response only.  |
| BROADCAST_MODE_ASYNC       | 3      | BROADCAST_MODE_ASYNC defines a tx broadcasting mode where the client returns immediately.                         |

### OrderBy

OrderBy defines the sorting order

| Name                   | Number | Description                                                                                      |
| ---------------------- | ------ | ------------------------------------------------------------------------------------------------ |
| ORDER_BY_UNSPECIFIED | 0      | ORDER_BY_UNSPECIFIED specifies an unknown sorting order. OrderBy defaults to ASC in this case. |
| ORDER_BY_ASC         | 1      | ORDER_BY_ASC defines ascending order                                                           |
| ORDER_BY_DESC        | 2      | ORDER_BY_DESC defines descending order                                                         |

### Service

Service defines a gRPC service for interacting with transactions.

| Method Name   | Request Type                                                             | Response Type                                                              | Description                                                          | HTTP Verb | Endpoint                      |
| ------------- | ------------------------------------------------------------------------ | -------------------------------------------------------------------------- | -------------------------------------------------------------------- | --------- | ----------------------------- |
| `Simulate`    | [SimulateRequest](tx.md#cosmos.tx.v1beta1.SimulateRequest)       | [SimulateResponse](tx.md#cosmos.tx.v1beta1.SimulateResponse)       | Simulate simulates executing a transaction for estimating gas usage. | POST      | /cosmos/tx/v1beta1/simulate   |
| `GetTx`       | [GetTxRequest](tx.md#cosmos.tx.v1beta1.GetTxRequest)             | [GetTxResponse](tx.md#cosmos.tx.v1beta1.GetTxResponse)             | GetTx fetches a tx by hash.                                          | GET       | /cosmos/tx/v1beta1/txs/{hash} |
| `BroadcastTx` | [BroadcastTxRequest](tx.md#cosmos.tx.v1beta1.BroadcastTxRequest) | [BroadcastTxResponse](tx.md#cosmos.tx.v1beta1.BroadcastTxResponse) | BroadcastTx broadcast transaction.                                   | POST      | /cosmos/tx/v1beta1/txs        |
| `GetTxsEvent` | [GetTxsEventRequest](tx.md#cosmos.tx.v1beta1.GetTxsEventRequest) | [GetTxsEventResponse](tx.md#cosmos.tx.v1beta1.GetTxsEventResponse) | GetTxsEvent fetches txs by event.                                    | GET       | /cosmos/tx/v1beta1/txs        |

