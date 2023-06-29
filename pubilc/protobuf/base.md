
## cosmos/base/v1beta1/coin.proto

### Coin

Coin defines a token with a denomination and an amount.

NOTE: The amount field is an Int which implements the custom method signatures required by gogoproto.

| Field    | Type                           | Label | Description |
| -------- | ------------------------------ | ----- | ----------- |
| `denom`  | [string](value.md#string) |       |             |
| `amount` | [string](value.md#string) |       |             |

### DecCoin

DecCoin defines a token with a denomination and a decimal amount.

NOTE: The amount field is an Dec which implements the custom method signatures required by gogoproto.

| Field    | Type                           | Label | Description |
| -------- | ------------------------------ | ----- | ----------- |
| `denom`  | [string](value.md#string) |       |             |
| `amount` | [string](value.md#string) |       |             |

### DecProto

DecProto defines a Protobuf wrapper around a Dec object.

| Field | Type                           | Label | Description |
| ----- | ------------------------------ | ----- | ----------- |
| `dec` | [string](value.md#string) |       |             |

### IntProto

IntProto defines a Protobuf wrapper around an Int object.

| Field | Type                           | Label | Description |
| ----- | ------------------------------ | ----- | ----------- |
| `int` | [string](value.md#string) |       |             |



## cosmos/base/query/v1beta1/pagination.proto

### PageRequest

PageRequest is to be embedded in gRPC request messages for efficient pagination. Ex:

message SomeRequest { Foo some_parameter = 1; PageRequest pagination = 2; }

| Field         | Type                           | Label | Description                                                                                                                                                                                                                         |
| ------------- | ------------------------------ | ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `key`         | [bytes](value.md#bytes)   |       | key is a value returned in PageResponse.next_key to begin querying the next page most efficiently. Only one of offset or key should be set.                                                                                        |
| `offset`      | [uint64](value.md#uint64) |       | offset is a numeric offset that can be used when key is unavailable. It is less efficient than using key. Only one of offset or key should be set.                                                                                  |
| `limit`       | [uint64](value.md#uint64) |       | limit is the total number of results to be returned in the result page. If left empty it will default to a value to be set by each app.                                                                                             |
| `count_total` | [bool](value.md#bool)     |       | count_total is set to true to indicate that the result set should include a count of the total number of items available for pagination in UIs. count_total is only respected when offset is used. It is ignored when key is set. |

### PageResponse

PageResponse is to be embedded in gRPC response messages where the corresponding request message has used PageRequest.

message SomeResponse { repeated Bar results = 1; PageResponse page = 2; }

| Field      | Type                           | Label | Description                                                                                                      |
| ---------- | ------------------------------ | ----- | ---------------------------------------------------------------------------------------------------------------- |
| `next_key` | [bytes](value.md#bytes)   |       | next_key is the key to be passed to PageRequest.key to query the next page most efficiently                     |
| `total`    | [uint64](value.md#uint64) |       | total is total number of results available if PageRequest.count_total was set, its value is undefined otherwise |

## cosmos/base/abci/v1beta1/abci.proto

### ABCIMessageLog

ABCIMessageLog defines a structure containing an indexed tx ABCI message log.

| Field       | Type                                                              | Label    | Description                                                                       |
| ----------- | ----------------------------------------------------------------- | -------- | --------------------------------------------------------------------------------- |
| `msg_index` | [uint32](value.md#uint32)                                    |          |                                                                                   |
| `log`       | [string](value.md#string)                                    |          |                                                                                   |
| `events`    | [StringEvent](base.md#cosmos.base.abci.v1beta1.StringEvent) | repeated | Events contains a slice of Event objects that were emitted during some execution. |

### Attribute

Attribute defines an attribute wrapper where the key and value are strings instead of raw bytes.

| Field   | Type                           | Label | Description |
| ------- | ------------------------------ | ----- | ----------- |
| `key`   | [string](value.md#string) |       |             |
| `value` | [string](value.md#string) |       |             |

### GasInfo

GasInfo defines tx execution gas context.

| Field        | Type                           | Label | Description                                                         |
| ------------ | ------------------------------ | ----- | ------------------------------------------------------------------- |
| `gas_wanted` | [uint64](value.md#uint64) |       | GasWanted is the maximum units of work we allow this tx to perform. |
| `gas_used`   | [uint64](value.md#uint64) |       | GasUsed is the amount of gas actually consumed.                     |

### MsgData

MsgData defines the data returned in a Result object during message execution.

| Field      | Type                           | Label | Description |
| ---------- | ------------------------------ | ----- | ----------- |
| `msg_type` | [string](value.md#string) |       |             |
| `data`     | [bytes](value.md#bytes)   |       |             |

### Result

Result is the union of ResponseFormat and ResponseCheckTx.

| Field    | Type                                                         | Label    | Description                                                                                                                                         |
| -------- | ------------------------------------------------------------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `data`   | [bytes](value.md#bytes)                                 |          | Data is any data returned from message or handler execution. It MUST be length prefixed in order to separate data from multiple message executions. |
| `log`    | [string](value.md#string)                               |          | Log contains the log information from message or handler execution.                                                                                 |
| `events` | [tendermint.abci.Event](tendermint.abci.Event) | repeated | Events contains a slice of Event objects that were emitted during message or handler execution.                                                     |

### SearchTxsResult

SearchTxsResult defines a structure for querying txs pageable

| Field         | Type                                                            | Label    | Description                         |
| ------------- | --------------------------------------------------------------- | -------- | ----------------------------------- |
| `total_count` | [uint64](value.md#uint64)                                  |          | Count of all txs                    |
| `count`       | [uint64](value.md#uint64)                                  |          | Count of txs in current page        |
| `page_number` | [uint64](value.md#uint64)                                  |          | Index of current page, start from 1 |
| `page_total`  | [uint64](value.md#uint64)                                  |          | Count of total pages                |
| `limit`       | [uint64](value.md#uint64)                                  |          | Max count txs per page              |
| `txs`         | [TxResponse](base.md#cosmos.base.abci.v1beta1.TxResponse) | repeated | List of txs in current page         |

### SimulationResponse

SimulationResponse defines the response generated when a transaction is successfully simulated.

| Field      | Type                                                      | Label | Description |
| ---------- | --------------------------------------------------------- | ----- | ----------- |
| `gas_info` | [GasInfo](base.md#cosmos.base.abci.v1beta1.GasInfo) |       |             |
| `result`   | [Result](base.md#cosmos.base.abci.v1beta1.Result)   |       |             |

### StringEvent

StringEvent defines en Event object wrapper where all the attributes contain key/value pairs that are strings instead of raw bytes.

| Field        | Type                                                          | Label    | Description |
| ------------ | ------------------------------------------------------------- | -------- | ----------- |
| `type`       | [string](value.md#string)                                |          |             |
| `attributes` | [Attribute](base.md#cosmos.base.abci.v1beta1.Attribute) | repeated |             |

### TxMsgData

TxMsgData defines a list of MsgData. A transaction will have a MsgData object for each message.

| Field  | Type                                                      | Label    | Description |
| ------ | --------------------------------------------------------- | -------- | ----------- |
| `data` | [MsgData](base.md#cosmos.base.abci.v1beta1.MsgData) | repeated |             |

### TxResponse

TxResponse defines a structure containing relevant tx data and metadata. The tags are stringified and the log is JSON decoded.

| Field        | Type                                                                    | Label    | Description                                                                                                                                                             |
| ------------ | ----------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `height`     | [int64](value.md#int64)                                            |          | The block height                                                                                                                                                        |
| `txhash`     | [string](value.md#string)                                          |          | The transaction hash.                                                                                                                                                   |
| `codespace`  | [string](value.md#string)                                          |          | Namespace for the Code                                                                                                                                                  |
| `code`       | [uint32](value.md#uint32)                                          |          | Response code.                                                                                                                                                          |
| `data`       | [string](value.md#string)                                          |          | Result bytes, if any.                                                                                                                                                   |
| `raw_log`    | [string](value.md#string)                                          |          | The output of the application's logger (raw string). May be non-deterministic.                                                                                          |
| `logs`       | [ABCIMessageLog](base.md#cosmos.base.abci.v1beta1.ABCIMessageLog) | repeated | The output of the application's logger (typed). May be non-deterministic.                                                                                               |
| `info`       | [string](value.md#string)                                          |          | Additional information. May be non-deterministic.                                                                                                                       |
| `gas_wanted` | [int64](value.md#int64)                                            |          | Amount of gas requested for transaction.                                                                                                                                |
| `gas_used`   | [int64](value.md#int64)                                            |          | Amount of gas consumed by transaction.                                                                                                                                  |
| `tx`         | google.protobuf.Any                |          | The request transaction bytes.                                                                                                                                          |
| `timestamp`  | [string](value.md#string)                                          |          | Time of the previous block. For heights > 1, it's the weighted median of the timestamps of the valid votes in the block.LastCommit. For height == 1, it's genesis time. |



## cosmos/base/kv/v1beta1/kv.proto

### Pair

Pair defines a key/value bytes tuple.

| Field   | Type                         | Label | Description |
| ------- | ---------------------------- | ----- | ----------- |
| `key`   | [bytes](value.md#bytes) |       |             |
| `value` | [bytes](value.md#bytes) |       |             |

### Pairs

Pairs defines a repeated slice of Pair objects.

| Field   | Type                                              | Label    | Description |
| ------- | ------------------------------------------------- | -------- | ----------- |
| `pairs` | [Pair](base.md#cosmos.base.kv.v1beta1.Pair) | repeated |             |



## cosmos/base/reflection/v1beta1/reflection.proto

### ListAllInterfacesRequest

ListAllInterfacesRequest is the request type of the ListAllInterfaces RPC.

### ListAllInterfacesResponse

ListAllInterfacesResponse is the response type of the ListAllInterfaces RPC.

| Field             | Type                           | Label    | Description                                                    |
| ----------------- | ------------------------------ | -------- | -------------------------------------------------------------- |
| `interface_names` | [string](value.md#string) | repeated | interface_names is an array of all the registered interfaces. |

### ListImplementationsRequest

ListImplementationsRequest is the request type of the ListImplementations RPC.

| Field            | Type                           | Label | Description                                                             |
| ---------------- | ------------------------------ | ----- | ----------------------------------------------------------------------- |
| `interface_name` | [string](value.md#string) |       | interface_name defines the interface to query the implementations for. |

### ListImplementationsResponse

ListImplementationsResponse is the response type of the ListImplementations RPC.

| Field                          | Type                           | Label    | Description |
| ------------------------------ | ------------------------------ | -------- | ----------- |
| `implementation_message_names` | [string](value.md#string) | repeated |             |

### ReflectionService

ReflectionService defines a service for interface reflection.

| Method Name           | Request Type                                                                                          | Response Type                                                                                           | Description                                                                       | HTTP Verb | Endpoint                                                                     |
| --------------------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------- | ---------------------------------------------------------------------------- |
| `ListAllInterfaces`   | [ListAllInterfacesRequest](base.md#cosmos.base.reflection.v1beta1.ListAllInterfacesRequest)     | [ListAllInterfacesResponse](base.md#cosmos.base.reflection.v1beta1.ListAllInterfacesResponse)     | ListAllInterfaces lists all the interfaces registered in the interface registry.  | GET       | /cosmos/base/reflection/v1beta1/interfaces                                   |
| `ListImplementations` | [ListImplementationsRequest](base.md#cosmos.base.reflection.v1beta1.ListImplementationsRequest) | [ListImplementationsResponse](base.md#cosmos.base.reflection.v1beta1.ListImplementationsResponse) | ListImplementations list all the concrete types that implement a given interface. | GET       | /cosmos/base/reflection/v1beta1/interfaces/{interface_name}/implementations |



## cosmos/base/snapshots/v1beta1/snapshot.proto

### Metadata

Metadata contains SDK-specific snapshot metadata.

| Field          | Type                         | Label    | Description          |
| -------------- | ---------------------------- | -------- | -------------------- |
| `chunk_hashes` | [bytes](value.md#bytes) | repeated | SHA-256 chunk hashes |

### Snapshot

Snapshot contains Tendermint state sync snapshot info.

| Field      | Type                                                             | Label | Description |
| ---------- | ---------------------------------------------------------------- | ----- | ----------- |
| `height`   | [uint64](value.md#uint64)                                   |       |             |
| `format`   | [uint32](value.md#uint32)                                   |       |             |
| `chunks`   | [uint32](value.md#uint32)                                   |       |             |
| `hash`     | [bytes](value.md#bytes)                                     |       |             |
| `metadata` | [Metadata](base.md#cosmos.base.snapshots.v1beta1.Metadata) |       |             |



## cosmos/base/store/v1beta1/commit_info.proto

### CommitID

CommitID defines the committment information when a specific store is committed.

| Field     | Type                         | Label | Description |
| --------- | ---------------------------- | ----- | ----------- |
| `version` | [int64](value.md#int64) |       |             |
| `hash`    | [bytes](value.md#bytes) |       |             |

### CommitInfo

CommitInfo defines commit information used by the multi-store when committing a version/height.

| Field         | Type                                                           | Label    | Description |
| ------------- | -------------------------------------------------------------- | -------- | ----------- |
| `version`     | [int64](value.md#int64)                                   |          |             |
| `store_infos` | [StoreInfo](base.md#cosmos.base.store.v1beta1.StoreInfo) | repeated |             |

### StoreInfo

StoreInfo defines store-specific commit information. It contains a reference between a store name and the commit ID.

| Field       | Type                                                         | Label | Description |
| ----------- | ------------------------------------------------------------ | ----- | ----------- |
| `name`      | [string](value.md#string)                               |       |             |
| `commit_id` | [CommitID](base.md#cosmos.base.store.v1beta1.CommitID) |       |             |



## cosmos/base/store/v1beta1/snapshot.proto

### SnapshotIAVLItem

SnapshotIAVLItem is an exported IAVL node.

| Field     | Type                         | Label | Description |
| --------- | ---------------------------- | ----- | ----------- |
| `key`     | [bytes](value.md#bytes) |       |             |
| `value`   | [bytes](value.md#bytes) |       |             |
| `version` | [int64](value.md#int64) |       |             |
| `height`  | [int32](value.md#int32) |       |             |

### SnapshotItem

SnapshotItem is an item contained in a rootmulti.Store snapshot.

| Field   | Type                                                                           | Label | Description |
| ------- | ------------------------------------------------------------------------------ | ----- | ----------- |
| `store` | [SnapshotStoreItem](base.md#cosmos.base.store.v1beta1.SnapshotStoreItem) |       |             |
| `iavl`  | [SnapshotIAVLItem](base.md#cosmos.base.store.v1beta1.SnapshotIAVLItem)   |       |             |

### SnapshotStoreItem

SnapshotStoreItem contains metadata about a snapshotted store.

| Field  | Type                           | Label | Description |
| ------ | ------------------------------ | ----- | ----------- |
| `name` | [string](value.md#string) |       |             |



## cosmos/base/tendermint/v1beta1/query.proto

### GetBlockByHeightRequest

GetBlockByHeightRequest is the request type for the Query/GetBlockByHeight RPC method.

| Field    | Type                         | Label | Description |
| -------- | ---------------------------- | ----- | ----------- |
| `height` | [int64](value.md#int64) |       |             |

### GetBlockByHeightResponse

GetBlockByHeightResponse is the response type for the Query/GetBlockByHeight RPC method.

| Field      | Type                                                               | Label | Description |
| ---------- | ------------------------------------------------------------------ | ----- | ----------- |
| `block_id` | [tendermint.types.BlockID](tendermint.types.BlockID) |       |             |
| `block`    | [tendermint.types.Block](tendermint.types.Block)     |       |             |

### GetLatestBlockRequest

GetLatestBlockRequest is the request type for the Query/GetLatestBlock RPC method.

### GetLatestBlockResponse

GetLatestBlockResponse is the response type for the Query/GetLatestBlock RPC method.

| Field      | Type                                                               | Label | Description |
| ---------- | ------------------------------------------------------------------ | ----- | ----------- |
| `block_id` | [tendermint.types.BlockID](tendermint.types.BlockID) |       |             |
| `block`    | [tendermint.types.Block](tendermint.types.Block)     |       |             |

### GetLatestValidatorSetRequest

GetLatestValidatorSetRequest is the request type for the Query/GetValidatorSetByHeight RPC method.

| Field        | Type                                                                                         | Label | Description                                       |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ------------------------------------------------- |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an pagination for the request. |

### GetLatestValidatorSetResponse

GetLatestValidatorSetResponse is the response type for the Query/GetValidatorSetByHeight RPC method.

| Field          | Type                                                                                           | Label    | Description                                        |
| -------------- | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `block_height` | [int64](value.md#int64)                                                                   |          |                                                    |
| `validators`   | [Validator](base.md#cosmos.base.tendermint.v1beta1.Validator)                            | repeated |                                                    |
| `pagination`   | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines an pagination for the response. |

### GetNodeInfoRequest

GetNodeInfoRequest is the request type for the Query/GetNodeInfo RPC method.

### GetNodeInfoResponse

GetNodeInfoResponse is the request type for the Query/GetNodeInfo RPC method.

| Field                 | Type                                                                           | Label | Description |
| --------------------- | ------------------------------------------------------------------------------ | ----- | ----------- |
| `default_node_info`   | [tendermint.p2p.DefaultNodeInfo](tendermint.p2p.DefaultNodeInfo) |       |             |
| `application_version` | [VersionInfo](base.md#cosmos.base.tendermint.v1beta1.VersionInfo)        |       |             |

### GetSyncingRequest

GetSyncingRequest is the request type for the Query/GetSyncing RPC method.

### GetSyncingResponse

GetSyncingResponse is the response type for the Query/GetSyncing RPC method.

| Field     | Type                       | Label | Description |
| --------- | -------------------------- | ----- | ----------- |
| `syncing` | [bool](value.md#bool) |       |             |

### GetValidatorSetByHeightRequest

GetValidatorSetByHeightRequest is the request type for the Query/GetValidatorSetByHeight RPC method.

| Field        | Type                                                                                         | Label | Description                                       |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ------------------------------------------------- |
| `height`     | [int64](value.md#int64)                                                                 |       |                                                   |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an pagination for the request. |

### GetValidatorSetByHeightResponse

GetValidatorSetByHeightResponse is the response type for the Query/GetValidatorSetByHeight RPC method.

| Field          | Type                                                                                           | Label    | Description                                        |
| -------------- | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `block_height` | [int64](value.md#int64)                                                                   |          |                                                    |
| `validators`   | [Validator](base.md#cosmos.base.tendermint.v1beta1.Validator)                            | repeated |                                                    |
| `pagination`   | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines an pagination for the response. |

### Module

Module is the type for VersionInfo

| Field     | Type                           | Label | Description    |
| --------- | ------------------------------ | ----- | -------------- |
| `path`    | [string](value.md#string) |       | module path    |
| `version` | [string](value.md#string) |       | module version |
| `sum`     | [string](value.md#string) |       | checksum       |

### Validator

Validator is the type for the validator-set.

| Field               | Type                                                     | Label | Description |
| ------------------- | -------------------------------------------------------- | ----- | ----------- |
| `address`           | [string](value.md#string)                           |       |             |
| `pub_key`           | google.protobuf.Any |       |             |
| `voting_power`      | [int64](value.md#int64)                             |       |             |
| `proposer_priority` | [int64](value.md#int64)                             |       |             |

### VersionInfo

VersionInfo is the type for the GetNodeInfoResponse message.

| Field                | Type                                                          | Label    | Description |
| -------------------- | ------------------------------------------------------------- | -------- | ----------- |
| `name`               | [string](value.md#string)                                |          |             |
| `app_name`           | [string](value.md#string)                                |          |             |
| `version`            | [string](value.md#string)                                |          |             |
| `git_commit`         | [string](value.md#string)                                |          |             |
| `build_tags`         | [string](value.md#string)                                |          |             |
| `go_version`         | [string](value.md#string)                                |          |             |
| `build_deps`         | [Module](base.md#cosmos.base.tendermint.v1beta1.Module) | repeated |             |
| `cosmos_sdk_version` | [string](value.md#string)                                |          |             |

### Service

Service defines the gRPC querier service for tendermint queries.

| Method Name               | Request Type                                                                                                  | Response Type                                                                                                   | Description                                                      | HTTP Verb | Endpoint                                               |
| ------------------------- | ------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- | --------- | ------------------------------------------------------ |
| `GetNodeInfo`             | [GetNodeInfoRequest](base.md#cosmos.base.tendermint.v1beta1.GetNodeInfoRequest)                         | [GetNodeInfoResponse](base.md#cosmos.base.tendermint.v1beta1.GetNodeInfoResponse)                         | GetNodeInfo queries the current node info.                       | GET       | /cosmos/base/tendermint/v1beta1/node_info             |
| `GetSyncing`              | [GetSyncingRequest](base.md#cosmos.base.tendermint.v1beta1.GetSyncingRequest)                           | [GetSyncingResponse](base.md#cosmos.base.tendermint.v1beta1.GetSyncingResponse)                           | GetSyncing queries node syncing.                                 | GET       | /cosmos/base/tendermint/v1beta1/syncing                |
| `GetLatestBlock`          | [GetLatestBlockRequest](base.md#cosmos.base.tendermint.v1beta1.GetLatestBlockRequest)                   | [GetLatestBlockResponse](base.md#cosmos.base.tendermint.v1beta1.GetLatestBlockResponse)                   | GetLatestBlock returns the latest block.                         | GET       | /cosmos/base/tendermint/v1beta1/blocks/latest          |
| `GetBlockByHeight`        | [GetBlockByHeightRequest](base.md#cosmos.base.tendermint.v1beta1.GetBlockByHeightRequest)               | [GetBlockByHeightResponse](base.md#cosmos.base.tendermint.v1beta1.GetBlockByHeightResponse)               | GetBlockByHeight queries block for given height.                 | GET       | /cosmos/base/tendermint/v1beta1/blocks/{height}        |
| `GetLatestValidatorSet`   | [GetLatestValidatorSetRequest](base.md#cosmos.base.tendermint.v1beta1.GetLatestValidatorSetRequest)     | [GetLatestValidatorSetResponse](base.md#cosmos.base.tendermint.v1beta1.GetLatestValidatorSetResponse)     | GetLatestValidatorSet queries latest validator-set.              | GET       | /cosmos/base/tendermint/v1beta1/validatorsets/latest   |
| `GetValidatorSetByHeight` | [GetValidatorSetByHeightRequest](base.md#cosmos.base.tendermint.v1beta1.GetValidatorSetByHeightRequest) | [GetValidatorSetByHeightResponse](base.md#cosmos.base.tendermint.v1beta1.GetValidatorSetByHeightResponse) | GetValidatorSetByHeight queries validator-set at a given height. | GET       | /cosmos/base/tendermint/v1beta1/validatorsets/{height} |


