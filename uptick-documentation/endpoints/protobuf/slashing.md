
## cosmos/slashing/v1beta1/slashing.proto

### Params

Params represents the parameters used for by the slashing module.

| Field                        | Type                                                               | Label | Description |
| ---------------------------- | ------------------------------------------------------------------ | ----- | ----------- |
| `signed_blocks_window`       | [int64](value.md#int64)                                       |       |             |
| `min_signed_per_window`      | [bytes](value.md#bytes)                                       |       |             |
| `downtime_jail_duration`     | google.protobuf.Duration |       |             |
| `slash_fraction_double_sign` | [bytes](value.md#bytes)                                       |       |             |
| `slash_fraction_downtime`    | [bytes](value.md#bytes)                                       |       |             |

### ValidatorSigningInfo

ValidatorSigningInfo defines a validator's signing info for monitoring their liveness activity.

| Field                   | Type                                                                 | Label | Description                                                                  |
| ----------------------- | -------------------------------------------------------------------- | ----- | ---------------------------------------------------------------------------- |
| `address`               | [string](value.md#string)                                       |       |                                                                              |
| `start_height`          | [int64](value.md#int64)                                         |       | height at which validator was first a candidate OR was unjailed              |
| `index_offset`          | [int64](value.md#int64)                                         |       | index offset into signed block bit array                                     |
| `jailed_until`          | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |       | timestamp validator cannot be unjailed until                                 |
| `tombstoned`            | [bool](value.md#bool)                                           |       | whether or not a validator has been tombstoned (killed out of validator set) |
| `missed_blocks_counter` | [int64](value.md#int64)                                         |       | missed blocks counter (to avoid scanning the array every time)               |



## cosmos/slashing/v1beta1/genesis.proto

### GenesisState

GenesisState defines the slashing module's genesis state.

| Field           | Type                                                                                 | Label    | Description                                                                          |
| --------------- | ------------------------------------------------------------------------------------ | -------- | ------------------------------------------------------------------------------------ |
| `params`        | [Params](slashing.md#cosmos.slashing.v1beta1.Params)                               |          | params defines all the paramaters of related to deposit.                             |
| `signing_infos` | [SigningInfo](slashing.md#cosmos.slashing.v1beta1.SigningInfo)                     | repeated | signing_infos represents a map between validator addresses and their signing infos. |
| `missed_blocks` | [ValidatorMissedBlocks](slashing.md#cosmos.slashing.v1beta1.ValidatorMissedBlocks) | repeated | signing_infos represents a map between validator addresses and their missed blocks. |

### MissedBlock

MissedBlock contains height and missed status as boolean.

| Field    | Type                         | Label | Description                                        |
| -------- | ---------------------------- | ----- | -------------------------------------------------- |
| `index`  | [int64](value.md#int64) |       | index is the height at which the block was missed. |
| `missed` | [bool](value.md#bool)   |       | missed is the missed status.                       |

### SigningInfo

SigningInfo stores validator signing info of corresponding address.

| Field                    | Type                                                                               | Label | Description                                                             |
| ------------------------ | ---------------------------------------------------------------------------------- | ----- | ----------------------------------------------------------------------- |
| `address`                | [string](value.md#string)                                                     |       | address is the validator address.                                       |
| `validator_signing_info` | [ValidatorSigningInfo](slashing.md#cosmos.slashing.v1beta1.ValidatorSigningInfo) |       | validator_signing_info represents the signing info of this validator. |

### ValidatorMissedBlocks

ValidatorMissedBlocks contains array of missed blocks of corresponding address.

| Field           | Type                                                             | Label    | Description                                                   |
| --------------- | ---------------------------------------------------------------- | -------- | ------------------------------------------------------------- |
| `address`       | [string](value.md#string)                                   |          | address is the validator address.                             |
| `missed_blocks` | [MissedBlock](slashing.md#cosmos.slashing.v1beta1.MissedBlock) | repeated | missed_blocks is an array of missed blocks by the validator. |



## cosmos/slashing/v1beta1/query.proto

### QueryParamsRequest

QueryParamsRequest is the request type for the Query/Params RPC method

### QueryParamsResponse

QueryParamsResponse is the response type for the Query/Params RPC method

| Field    | Type                                                   | Label | Description |
| -------- | ------------------------------------------------------ | ----- | ----------- |
| `params` | [Params](slashing.md#cosmos.slashing.v1beta1.Params) |       |             |

### QuerySigningInfoRequest

QuerySigningInfoRequest is the request type for the Query/SigningInfo RPC method

| Field          | Type                           | Label | Description                                           |
| -------------- | ------------------------------ | ----- | ----------------------------------------------------- |
| `cons_address` | [string](value.md#string) |       | cons_address is the address to query signing info of |

### QuerySigningInfoResponse

QuerySigningInfoResponse is the response type for the Query/SigningInfo RPC method

| Field              | Type                                                                               | Label | Description                                                          |
| ------------------ | ---------------------------------------------------------------------------------- | ----- | -------------------------------------------------------------------- |
| `val_signing_info` | [ValidatorSigningInfo](slashing.md#cosmos.slashing.v1beta1.ValidatorSigningInfo) |       | val_signing_info is the signing info of requested val cons address |

### QuerySigningInfosRequest

QuerySigningInfosRequest is the request type for the Query/SigningInfos RPC method

| Field        | Type                                                                                         | Label | Description |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ----------- |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       |             |

### QuerySigningInfosResponse

QuerySigningInfosResponse is the response type for the Query/SigningInfos RPC method

| Field        | Type                                                                                           | Label    | Description                                |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | ------------------------------------------ |
| `info`       | [ValidatorSigningInfo](slashing.md#cosmos.slashing.v1beta1.ValidatorSigningInfo)             | repeated | info is the signing info of all validators |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          |                                            |

### Query

Query provides defines the gRPC querier service

| Method Name    | Request Type                                                                               | Response Type                                                                                | Description                                                | HTTP Verb | Endpoint                                                |
| -------------- | ------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- | ---------------------------------------------------------- | --------- | ------------------------------------------------------- |
| `Params`       | [QueryParamsRequest](slashing.md#cosmos.slashing.v1beta1.QueryParamsRequest)             | [QueryParamsResponse](slashing.md#cosmos.slashing.v1beta1.QueryParamsResponse)             | Params queries the parameters of slashing module           | GET       | /cosmos/slashing/v1beta1/params                         |
| `SigningInfo`  | [QuerySigningInfoRequest](slashing.md#cosmos.slashing.v1beta1.QuerySigningInfoRequest)   | [QuerySigningInfoResponse](slashing.md#cosmos.slashing.v1beta1.QuerySigningInfoResponse)   | SigningInfo queries the signing info of given cons address | GET       | /cosmos/slashing/v1beta1/signing_infos/{cons_address} |
| `SigningInfos` | [QuerySigningInfosRequest](slashing.md#cosmos.slashing.v1beta1.QuerySigningInfosRequest) | [QuerySigningInfosResponse](slashing.md#cosmos.slashing.v1beta1.QuerySigningInfosResponse) | SigningInfos queries signing info of all validators        | GET       | /cosmos/slashing/v1beta1/signing_infos                 |



## cosmos/slashing/v1beta1/tx.proto

### MsgUnjail

MsgUnjail defines the Msg/Unjail request type

| Field            | Type                           | Label | Description |
| ---------------- | ------------------------------ | ----- | ----------- |
| `validator_addr` | [string](value.md#string) |       |             |

### MsgUnjailResponse

MsgUnjailResponse defines the Msg/Unjail response type

### Msg

Msg defines the slashing Msg service.

| Method Name | Request Type                                                 | Response Type                                                                | Description                                                                                                                                                            | HTTP Verb | Endpoint |
| ----------- | ------------------------------------------------------------ | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- | -------- |
| `Unjail`    | [MsgUnjail](slashing.md#cosmos.slashing.v1beta1.MsgUnjail) | [MsgUnjailResponse](slashing.md#cosmos.slashing.v1beta1.MsgUnjailResponse) | Unjail defines a method for unjailing a jailed validator, thus returning them into the bonded validator set, so they can begin receiving provisions and rewards again. |           |          |

