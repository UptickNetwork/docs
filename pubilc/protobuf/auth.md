## cosmos/auth/v1beta1/auth.proto

### BaseAccount

BaseAccount defines a base account type. It contains all the necessary fields for basic account functionality. Any custom account type should extend this type for additional functionality (e.g. vesting).

| Field            | Type                                                     | Label | Description |
| ---------------- | -------------------------------------------------------- | ----- | ----------- |
| `address`        | [string](value.md#string)                           |       |             |
| `pub_key`        | google.protobuf.Any |       |             |
| `account_number` | [uint64](value.md#uint64)                           |       |             |
| `sequence`       | [uint64](value.md#uint64)                           |       |             |

### ModuleAccount

ModuleAccount defines an account for modules that holds coins on a pool.

| Field          | Type                                                         | Label    | Description |
| -------------- | ------------------------------------------------------------ | -------- | ----------- |
| `base_account` | [BaseAccount](auth.md#cosmos.auth.v1beta1.BaseAccount) |          |             |
| `name`         | [string](value.md#string)                               |          |             |
| `permissions`  | [string](value.md#string)                               | repeated |             |

### Params

Params defines the parameters for the auth module.

| Field                       | Type                           | Label | Description |
| --------------------------- | ------------------------------ | ----- | ----------- |
| `max_memo_characters`       | [uint64](value.md#uint64) |       |             |
| `tx_sig_limit`              | [uint64](value.md#uint64) |       |             |
| `tx_size_cost_per_byte`     | [uint64](value.md#uint64) |       |             |
| `sig_verify_cost_ed25519`   | [uint64](value.md#uint64) |       |             |
| `sig_verify_cost_secp256k1` | [uint64](value.md#uint64) |       |             |



## cosmos/auth/v1beta1/genesis.proto

### GenesisState

GenesisState defines the auth module's genesis state.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `params`   | [Params](auth.md#cosmos.auth.v1beta1.Params)       |          | params defines all the paramaters of the module. |
| `accounts` | google.protobuf.Any | repeated | accounts are the accounts present at genesis.    |



## cosmos/auth/v1beta1/query.proto

### QueryAccountRequest

QueryAccountRequest is the request type for the Query/Account RPC method.

| Field     | Type                           | Label | Description                               |
| --------- | ------------------------------ | ----- | ----------------------------------------- |
| `address` | [string](value.md#string) |       | address defines the address to query for. |

### QueryAccountResponse

QueryAccountResponse is the response type for the Query/Account RPC method.

| Field     | Type                                                     | Label | Description                                               |
| --------- | -------------------------------------------------------- | ----- | --------------------------------------------------------- |
| `account` | google.protobuf.Any |       | account defines the account of the corresponding address. |

### QueryParamsRequest

QueryParamsRequest is the request type for the Query/Params RPC method.

### QueryParamsResponse

QueryParamsResponse is the response type for the Query/Params RPC method.

| Field    | Type                                               | Label | Description                                  |
| -------- | -------------------------------------------------- | ----- | -------------------------------------------- |
| `params` | [Params](auth.md#cosmos.auth.v1beta1.Params) |       | params defines the parameters of the module. |

### Query

Query defines the gRPC querier service.

| Method Name | Request Type                                                                 | Response Type                                                                  | Description                                       | HTTP Verb | Endpoint                                |
| ----------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------- | --------- | --------------------------------------- |
| `Account`   | [QueryAccountRequest](auth.md#cosmos.auth.v1beta1.QueryAccountRequest) | [QueryAccountResponse](auth.md#cosmos.auth.v1beta1.QueryAccountResponse) | Account returns account details based on address. | GET       | /cosmos/auth/v1beta1/accounts/{address} |
| `Params`    | [QueryParamsRequest](auth.md#cosmos.auth.v1beta1.QueryParamsRequest)   | [QueryParamsResponse](auth.md#cosmos.auth.v1beta1.QueryParamsResponse)   | Params queries all parameters.                    | GET       | /cosmos/auth/v1beta1/params             |

