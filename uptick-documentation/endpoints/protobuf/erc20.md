## uptick/erc20/v1/erc20.proto

### RegisterCoinProposal

RegisterCoinProposal is a gov Content type to register a token pair

| Field         | Type                                                                       | Label | Description                                               |
| ------------- | -------------------------------------------------------------------------- | ----- | --------------------------------------------------------- |
| `title`       | [string](value.md#string)                                             |       | title of the proposal                                     |
| `description` | [string](value.md#string)                                             |       | proposal description                                      |
| `metadata`    | [cosmos.bank.v1beta1.Metadata](bank.md#cosmos.bank.v1beta1.Metadata) |       | token pair of Cosmos native denom and ERC20 token address |

### RegisterERC20Proposal

RegisterCoinProposal is a gov Content type to register a token pair

| Field          | Type                           | Label | Description                     |
| -------------- | ------------------------------ | ----- | ------------------------------- |
| `title`        | [string](value.md#string) |       | title of the proposal           |
| `description`  | [string](value.md#string) |       | proposal description            |
| `erc20address` | [string](value.md#string) |       | contract address of ERC20 token |

### ToggleTokenRelayProposal

ToggleTokenRelayProposal is a gov Content type to toggle the internal relaying of a token pair.

| Field         | Type                           | Label | Description                                                                                          |
| ------------- | ------------------------------ | ----- | ---------------------------------------------------------------------------------------------------- |
| `title`       | [string](value.md#string) |       | title of the proposal                                                                                |
| `description` | [string](value.md#string) |       | proposal description                                                                                 |
| `token`       | [string](value.md#string) |       | token identifier can be either the hex contract address of the ERC20 or the Cosmos base denomination |

### TokenPair

TokenPair defines an instance that records pairing consisting of a Cosmos native Coin and an ERC20 token address.

| Field            | Type                                         | Label | Description                                                               |
| ---------------- | -------------------------------------------- | ----- | ------------------------------------------------------------------------- |
| `erc20_address`  | [string](value.md#string)               |       | address of ERC20 contract token                                           |
| `denom`          | [string](value.md#string)               |       | cosmos base denomination to be mapped to                                  |
| `enabled`        | [bool](value.md#bool)                   |       | shows token mapping enable status                                         |
| `contract_owner` | [Owner](erc20.md#uptick.erc20.v1.Owner) |       | ERC20 owner address ENUM (0 invalid, 1 ModuleAccount, 2 external address) |

### UpdateTokenPairERC20Proposal

UpdateTokenPairERC20Proposal is a gov Content type to update a token pair's ERC20 contract address.

| Field               | Type                           | Label | Description                         |
| ------------------- | ------------------------------ | ----- | ----------------------------------- |
| `title`             | [string](value.md#string) |       | title of the proposal               |
| `description`       | [string](value.md#string) |       | proposal description                |
| `erc20_address`     | [string](value.md#string) |       | contract address of ERC20 token     |
| `new_erc20_address` | [string](value.md#string) |       | new address of ERC20 token contract |

### Owner

Owner enumerates the ownership of a ERC20 contract.

| Name               | Number | Description                                               |
| ------------------ | ------ | --------------------------------------------------------- |
| OWNER_UNSPECIFIED | 0      | OWNER_UNSPECIFIED defines an invalid/undefined owner.    |
| OWNER_MODULE      | 1      | OWNER_MODULE erc20 is owned by the erc20 module account. |
| OWNER_EXTERNAL    | 2      | EXTERNAL erc20 is owned by an external account.           |



## uptick/erc20/v1/genesis.proto

### GenesisState

GenesisState defines the module's genesis state.

| Field         | Type                                                 | Label    | Description            |
| ------------- | ---------------------------------------------------- | -------- | ---------------------- |
| `params`      | [Params](erc20.md#uptick.erc20.v1.Params)       |          | module parameters      |
| `token_pairs` | [TokenPair](erc20.md#uptick.erc20.v1.TokenPair) | repeated | registered token pairs |

### Params

Params defines the erc20 module params

| Field             | Type                       | Label | Description                                                                                                                                                           |
| ----------------- | -------------------------- | ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `enable_erc20`    | [bool](value.md#bool) |       | parameter to enable the intrarelaying of Cosmos coins <--> ERC20 tokens.                                                                                              |
| `enable_evm_hook` | [bool](value.md#bool) |       | parameter to enable the EVM hook to convert an ERC20 token to a Cosmos Coin by transferring the Tokens through a MsgEthereumTx to the ModuleAddress Ethereum address. |



## uptick/erc20/v1/query.proto

### QueryParamsRequest

QueryParamsRequest is the request type for the Query/Params RPC method.

### QueryParamsResponse

QueryParamsResponse is the response type for the Query/Params RPC method.

| Field    | Type                                           | Label | Description |
| -------- | ---------------------------------------------- | ----- | ----------- |
| `params` | [Params](erc20.md#uptick.erc20.v1.Params) |       |             |

### QueryTokenPairRequest

QueryTokenPairRequest is the request type for the Query/TokenPair RPC method.

| Field   | Type                           | Label | Description                                                                                          |
| ------- | ------------------------------ | ----- | ---------------------------------------------------------------------------------------------------- |
| `token` | [string](value.md#string) |       | token identifier can be either the hex contract address of the ERC20 or the Cosmos base denomination |

### QueryTokenPairResponse

QueryTokenPairResponse is the response type for the Query/TokenPair RPC method.

| Field        | Type                                                 | Label | Description |
| ------------ | ---------------------------------------------------- | ----- | ----------- |
| `token_pair` | [TokenPair](erc20.md#uptick.erc20.v1.TokenPair) |       |             |

### QueryTokenPairsRequest

QueryTokenPairsRequest is the request type for the Query/TokenPairs RPC method.

| Field        | Type                                                                                         | Label | Description                                                |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request. |

### QueryTokenPairsResponse

QueryTokenPairsResponse is the response type for the Query/TokenPairs RPC method.

| Field         | Type                                                                                           | Label    | Description                                        |
| ------------- | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `token_pairs` | [TokenPair](erc20.md#uptick.erc20.v1.TokenPair)                                           | repeated |                                                    |
| `pagination`  | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### Query

Query defines the gRPC querier service.

| Method Name  | Request Type                                                                   | Response Type                                                                    | Description                              | HTTP Verb | Endpoint                              |
| ------------ | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------- | ---------------------------------------- | --------- | ------------------------------------- |
| `TokenPairs` | [QueryTokenPairsRequest](erc20.md#uptick.erc20.v1.QueryTokenPairsRequest) | [QueryTokenPairsResponse](erc20.md#uptick.erc20.v1.QueryTokenPairsResponse) | Retrieves registered token pairs         | GET       | /uptick/erc20/v1/token_pairs         |
| `TokenPair`  | [QueryTokenPairRequest](erc20.md#uptick.erc20.v1.QueryTokenPairRequest)   | [QueryTokenPairResponse](erc20.md#uptick.erc20.v1.QueryTokenPairResponse)   | Retrieves a registered token pair        | GET       | /uptick/erc20/v1/token_pairs/{token} |
| `Params`     | [QueryParamsRequest](erc20.md#uptick.erc20.v1.QueryParamsRequest)         | [QueryParamsResponse](erc20.md#uptick.erc20.v1.QueryParamsResponse)         | Params retrieves the erc20 module params | GET       | /uptick/erc20/v1/params               |



## uptick/erc20/v1/tx.proto

### MsgConvertCoin

MsgConvertCoin defines a Msg to convert a Cosmos Coin to a ERC20 token

| Field      | Type                                                               | Label | Description                                                                                                              |
| ---------- | ------------------------------------------------------------------ | ----- | ------------------------------------------------------------------------------------------------------------------------ |
| `coin`     | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) |       | Cosmos coin which denomination is registered on erc20 bridge. The coin amount defines the total ERC20 tokens to convert. |
| `receiver` | [string](value.md#string)                                     |       | recipient hex address to receive ERC20 token                                                                             |
| `sender`   | [string](value.md#string)                                     |       | cosmos bech32 address from the owner of the given ERC20 tokens                                                           |

### MsgConvertCoinResponse

MsgConvertCoinResponse returns no fields

### MsgConvertERC20

MsgConvertERC20 defines a Msg to convert an ERC20 token to a Cosmos SDK coin.

| Field              | Type                           | Label | Description                                                 |
| ------------------ | ------------------------------ | ----- | ----------------------------------------------------------- |
| `contract_address` | [string](value.md#string) |       | ERC20 token contract address registered on erc20 bridge     |
| `amount`           | [string](value.md#string) |       | amount of ERC20 tokens to mint                              |
| `receiver`         | [string](value.md#string) |       | bech32 address to receive SDK coins.                        |
| `sender`           | [string](value.md#string) |       | sender hex address from the owner of the given ERC20 tokens |

### MsgConvertERC20Response

MsgConvertERC20Response returns no fields

### Msg

Msg defines the erc20 Msg service.

| Method Name    | Request Type                                                     | Response Type                                                                    | Description                                                                                                          | HTTP Verb | Endpoint                           |
| -------------- | ---------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- | ---------------------------------- |
| `ConvertCoin`  | [MsgConvertCoin](erc20.md#uptick.erc20.v1.MsgConvertCoin)   | [MsgConvertCoinResponse](erc20.md#uptick.erc20.v1.MsgConvertCoinResponse)   | ConvertCoin mints a ERC20 representation of the SDK Coin denom that is registered on the token mapping.              | GET       | /uptick/erc20/v1/tx/convert_coin  |
| `ConvertERC20` | [MsgConvertERC20](erc20.md#uptick.erc20.v1.MsgConvertERC20) | [MsgConvertERC20Response](erc20.md#uptick.erc20.v1.MsgConvertERC20Response) | ConvertERC20 mints a Cosmos coin representation of the ERC20 token contract that is registered on the token mapping. | GET       | /uptick/erc20/v1/tx/convert_erc20 |

