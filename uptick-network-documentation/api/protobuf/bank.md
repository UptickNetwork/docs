## cosmos/bank/v1beta1/bank.proto

### DenomUnit

DenomUnit represents a struct that describes a given denomination unit of the basic token.

| Field      | Type                           | Label    | Description                                                                                                                                                                                                                                                                           |
| ---------- | ------------------------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `denom`    | [string](value.md#string) |          | denom represents the string name of the given denom unit (e.g uatom).                                                                                                                                                                                                                 |
| `exponent` | [uint32](value.md#uint32) |          | exponent represents power of 10 exponent that one must raise the base_denom to in order to equal the given DenomUnit's denom 1 denom = 1^exponent base_denom (e.g. with a base_denom of uatom, one can create a DenomUnit of 'atom' with exponent = 6, thus: 1 atom = 10^6 uatom). |
| `aliases`  | [string](value.md#string) | repeated | aliases is a list of string aliases for the given denom                                                                                                                                                                                                                               |

### Input

Input models transaction input.

| Field     | Type                                                               | Label    | Description |
| --------- | ------------------------------------------------------------------ | -------- | ----------- |
| `address` | [string](value.md#string)                                     |          |             |
| `coins`   | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |

### Metadata

Metadata represents a struct that describes a basic token.

| Field         | Type                                                     | Label    | Description                                                                 |
| ------------- | -------------------------------------------------------- | -------- | --------------------------------------------------------------------------- |
| `description` | [string](value.md#string)                           |          |                                                                             |
| `denom_units` | [DenomUnit](bank.md#cosmos.bank.v1beta1.DenomUnit) | repeated | denom_units represents the list of DenomUnit's for a given coin            |
| `base`        | [string](value.md#string)                           |          | base represents the base denom (should be the DenomUnit with exponent = 0). |
| `display`     | [string](value.md#string)                           |          | display indicates the suggested denom that should be displayed in clients.  |

### Output

Output models transaction outputs.

| Field     | Type                                                               | Label    | Description |
| --------- | ------------------------------------------------------------------ | -------- | ----------- |
| `address` | [string](value.md#string)                                     |          |             |
| `coins`   | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |

### Params

Params defines the parameters for the bank module.

| Field                  | Type                                                         | Label    | Description |
| ---------------------- | ------------------------------------------------------------ | -------- | ----------- |
| `send_enabled`         | [SendEnabled](bank.md#cosmos.bank.v1beta1.SendEnabled) | repeated |             |
| `default_send_enabled` | [bool](value.md#bool)                                   |          |             |

### SendEnabled

SendEnabled maps coin denom to a send_enabled status (whether a denom is sendable).

| Field     | Type                           | Label | Description |
| --------- | ------------------------------ | ----- | ----------- |
| `denom`   | [string](value.md#string) |       |             |
| `enabled` | [bool](value.md#bool)     |       |             |

### Supply

Supply represents a struct that passively keeps track of the total supply amounts in the network.

| Field   | Type                                                               | Label    | Description |
| ------- | ------------------------------------------------------------------ | -------- | ----------- |
| `total` | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |



## cosmos/bank/v1beta1/genesis.proto

### Balance

Balance defines an account address and balance pair used in the bank module's genesis state.

| Field     | Type                                                               | Label    | Description                                           |
| --------- | ------------------------------------------------------------------ | -------- | ----------------------------------------------------- |
| `address` | [string](value.md#string)                                     |          | address is the address of the balance holder.         |
| `coins`   | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated | coins defines the different coins this balance holds. |

### GenesisState

GenesisState defines the bank module's genesis state.

| Field            | Type                                                               | Label    | Description                                                       |
| ---------------- | ------------------------------------------------------------------ | -------- | ----------------------------------------------------------------- |
| `params`         | [Params](bank.md#cosmos.bank.v1beta1.Params)                 |          | params defines all the paramaters of the module.                  |
| `balances`       | [Balance](bank.md#cosmos.bank.v1beta1.Balance)               | repeated | balances is an array containing the balances of all the accounts. |
| `supply`         | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated | supply represents the total supply.                               |
| `denom_metadata` | [Metadata](bank.md#cosmos.bank.v1beta1.Metadata)             | repeated | denom_metadata defines the metadata of the differents coins.     |



## cosmos/bank/v1beta1/query.proto

### QueryAllBalancesRequest

QueryBalanceRequest is the request type for the Query/AllBalances RPC method.

| Field        | Type                                                                                         | Label | Description                                                |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `address`    | [string](value.md#string)                                                               |       | address is the address to query balances for.              |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request. |

### QueryAllBalancesResponse

QueryAllBalancesResponse is the response type for the Query/AllBalances RPC method.

| Field        | Type                                                                                           | Label    | Description                                        |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `balances`   | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin)                             | repeated | balances is the balances of all the coins.         |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### QueryBalanceRequest

QueryBalanceRequest is the request type for the Query/Balance RPC method.

| Field     | Type                           | Label | Description                                    |
| --------- | ------------------------------ | ----- | ---------------------------------------------- |
| `address` | [string](value.md#string) |       | address is the address to query balances for.  |
| `denom`   | [string](value.md#string) |       | denom is the coin denom to query balances for. |

### QueryBalanceResponse

QueryBalanceResponse is the response type for the Query/Balance RPC method.

| Field     | Type                                                               | Label | Description                         |
| --------- | ------------------------------------------------------------------ | ----- | ----------------------------------- |
| `balance` | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) |       | balance is the balance of the coin. |

### QueryDenomMetadataRequest

QueryDenomMetadataRequest is the request type for the Query/DenomMetadata RPC method.

| Field   | Type                           | Label | Description                                        |
| ------- | ------------------------------ | ----- | -------------------------------------------------- |
| `denom` | [string](value.md#string) |       | denom is the coin denom to query the metadata for. |

### QueryDenomMetadataResponse

QueryDenomMetadataResponse is the response type for the Query/DenomMetadata RPC method.

| Field      | Type                                                   | Label | Description                                                                         |
| ---------- | ------------------------------------------------------ | ----- | ----------------------------------------------------------------------------------- |
| `metadata` | [Metadata](bank.md#cosmos.bank.v1beta1.Metadata) |       | metadata describes and provides all the client information for the requested token. |

### QueryDenomsMetadataRequest

QueryDenomsMetadataRequest is the request type for the Query/DenomsMetadata RPC method.

| Field        | Type                                                                                         | Label | Description                                                |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request. |

### QueryDenomsMetadataResponse

QueryDenomsMetadataResponse is the response type for the Query/DenomsMetadata RPC method.

| Field        | Type                                                                                           | Label    | Description                                                             |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------- |
| `metadatas`  | [Metadata](bank.md#cosmos.bank.v1beta1.Metadata)                                         | repeated | metadata provides the client information for all the registered tokens. |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response.                      |

### QueryParamsRequest

QueryParamsRequest defines the request type for querying x/bank parameters.

### QueryParamsResponse

QueryParamsResponse defines the response type for querying x/bank parameters.

| Field    | Type                                               | Label | Description |
| -------- | -------------------------------------------------- | ----- | ----------- |
| `params` | [Params](bank.md#cosmos.bank.v1beta1.Params) |       |             |

### QuerySupplyOfRequest

QuerySupplyOfRequest is the request type for the Query/SupplyOf RPC method.

| Field   | Type                           | Label | Description                                    |
| ------- | ------------------------------ | ----- | ---------------------------------------------- |
| `denom` | [string](value.md#string) |       | denom is the coin denom to query balances for. |

### QuerySupplyOfResponse

QuerySupplyOfResponse is the response type for the Query/SupplyOf RPC method.

| Field    | Type                                                               | Label | Description                       |
| -------- | ------------------------------------------------------------------ | ----- | --------------------------------- |
| `amount` | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) |       | amount is the supply of the coin. |

### QueryTotalSupplyRequest

QueryTotalSupplyRequest is the request type for the Query/TotalSupply RPC method.

### QueryTotalSupplyResponse

QueryTotalSupplyResponse is the response type for the Query/TotalSupply RPC method

| Field    | Type                                                               | Label    | Description                       |
| -------- | ------------------------------------------------------------------ | -------- | --------------------------------- |
| `supply` | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated | supply is the supply of the coins |

### Query

Query defines the gRPC querier service.

| Method Name      | Request Type                                                                               | Response Type                                                                                | Description                                                                       | HTTP Verb | Endpoint                                        |
| ---------------- | ------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------- | ----------------------------------------------- |
| `Balance`        | [QueryBalanceRequest](bank.md#cosmos.bank.v1beta1.QueryBalanceRequest)               | [QueryBalanceResponse](bank.md#cosmos.bank.v1beta1.QueryBalanceResponse)               | Balance queries the balance of a single coin for a single account.                | GET       | /cosmos/bank/v1beta1/balances/{address}/{denom} |
| `AllBalances`    | [QueryAllBalancesRequest](bank.md#cosmos.bank.v1beta1.QueryAllBalancesRequest)       | [QueryAllBalancesResponse](bank.md#cosmos.bank.v1beta1.QueryAllBalancesResponse)       | AllBalances queries the balance of all coins for a single account.                | GET       | /cosmos/bank/v1beta1/balances/{address}         |
| `TotalSupply`    | [QueryTotalSupplyRequest](bank.md#cosmos.bank.v1beta1.QueryTotalSupplyRequest)       | [QueryTotalSupplyResponse](bank.md#cosmos.bank.v1beta1.QueryTotalSupplyResponse)       | TotalSupply queries the total supply of all coins.                                | GET       | /cosmos/bank/v1beta1/supply                     |
| `SupplyOf`       | [QuerySupplyOfRequest](bank.md#cosmos.bank.v1beta1.QuerySupplyOfRequest)             | [QuerySupplyOfResponse](bank.md#cosmos.bank.v1beta1.QuerySupplyOfResponse)             | SupplyOf queries the supply of a single coin.                                     | GET       | /cosmos/bank/v1beta1/supply/{denom}             |
| `Params`         | [QueryParamsRequest](bank.md#cosmos.bank.v1beta1.QueryParamsRequest)                 | [QueryParamsResponse](bank.md#cosmos.bank.v1beta1.QueryParamsResponse)                 | Params queries the parameters of x/bank module.                                   | GET       | /cosmos/bank/v1beta1/params                     |
| `DenomMetadata`  | [QueryDenomMetadataRequest](bank.md#cosmos.bank.v1beta1.QueryDenomMetadataRequest)   | [QueryDenomMetadataResponse](bank.md#cosmos.bank.v1beta1.QueryDenomMetadataResponse)   | DenomsMetadata queries the client metadata of a given coin denomination.          | GET       | /cosmos/bank/v1beta1/denoms_metadata/{denom}   |
| `DenomsMetadata` | [QueryDenomsMetadataRequest](bank.md#cosmos.bank.v1beta1.QueryDenomsMetadataRequest) | [QueryDenomsMetadataResponse](bank.md#cosmos.bank.v1beta1.QueryDenomsMetadataResponse) | DenomsMetadata queries the client metadata for all registered coin denominations. | GET       | /cosmos/bank/v1beta1/denoms_metadata           |



## cosmos/bank/v1beta1/tx.proto

### MsgMultiSend

MsgMultiSend represents an arbitrary multi-in, multi-out send message.

| Field     | Type                                               | Label    | Description |
| --------- | -------------------------------------------------- | -------- | ----------- |
| `inputs`  | [Input](bank.md#cosmos.bank.v1beta1.Input)   | repeated |             |
| `outputs` | [Output](bank.md#cosmos.bank.v1beta1.Output) | repeated |             |

### MsgMultiSendResponse

MsgMultiSendResponse defines the Msg/MultiSend response type.

### MsgSend

MsgSend represents a message to send coins from one account to another.

| Field          | Type                                                               | Label    | Description |
| -------------- | ------------------------------------------------------------------ | -------- | ----------- |
| `from_address` | [string](value.md#string)                                     |          |             |
| `to_address`   | [string](value.md#string)                                     |          |             |
| `amount`       | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |

### MsgSendResponse

MsgSendResponse defines the Msg/Send response type.

### Msg

Msg defines the bank Msg service.

| Method Name | Request Type                                                   | Response Type                                                                  | Description                                                                        | HTTP Verb | Endpoint |
| ----------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------- | --------- | -------- |
| `Send`      | [MsgSend](bank.md#cosmos.bank.v1beta1.MsgSend)           | [MsgSendResponse](bank.md#cosmos.bank.v1beta1.MsgSendResponse)           | Send defines a method for sending coins from one account to another account.       |           |          |
| `MultiSend` | [MsgMultiSend](bank.md#cosmos.bank.v1beta1.MsgMultiSend) | [MsgMultiSendResponse](bank.md#cosmos.bank.v1beta1.MsgMultiSendResponse) | MultiSend defines a method for sending coins from some accounts to other accounts. |           |          |

