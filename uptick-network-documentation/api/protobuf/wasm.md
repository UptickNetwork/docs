## cosmwasm/wasm/v1/genesis.proto

### GenesisState

GenesisState - genesis state of x/wasm

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `params`   | [Params](wasm.md#Params)       |          | params defines the parameters of the module.  |
| `codes` | [Code](wasm.md#Code) | repeated |  |
| `contracts` | [Contract](wasm.md#Contract) | repeated |  |
| `sequences` | [Sequence](wasm.md#Sequence) | repeated | |
| `gen_msgs` | [GenMsgs](wasm.md#GenMsgs) | repeated |  |


### GenMsgs

GenMsgs define the messages that can be executed during genesis phase in order. The intention is to have more human readable data that is auditable. 

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `store_code`   | [MsgStoreCode](wasm.md#MsgStoreCode)       |          |  |
| `instantiate_contract` | [MsgInstantiateContract](wasm.md#MsgInstantiateContract) |  |  |
| `execute_contract` | [MsgExecuteContract](wasm.md#MsgExecuteContract) |  |  |

### Code

Code struct encompasses CodeInfo and CodeBytes

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_id`   | uint64      |          |  |
| `code_info` | [CodeInfo](wasm.md#CodeInfo) |  |   |
| `code_bytes` | bytes|  |  |
| `pinned` | bool|  | Pinned to wasmvm cache |


### Contract

Contract struct encompasses ContractAddress, ContractInfo, and ContractState

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_id`   | contract_address      |          |  |
| `contract_info` | [ContractInfo](wasm.md#ContractInfo) |  |   |
| `contract_state` | Model| repeated |  |

### Sequence

Contract struct encompasses ContractAddress, ContractInfo, and ContractState

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `id_key`   | bytes      |          |  |
| `value` | uint64 |  |   |



## cosmwasm/wasm/v1/ibc.proto

### MsgIBCSend

MsgIBCSend

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `channel`   | string      |          | the channel by which the packet will be sent |
| `timeout_height` | uint64 |  | Timeout height relative to the current block height.  |
| `timeout_timestamp` | uint64 |  | Timeout timestamp (in nanoseconds) relative to the current block timestamp.  |
| `data` | bytes |  | Data is the payload to transfer. We must not make assumption what format or content is in here. |


### MsgIBCCloseChannel

MsgIBCCloseChannel port and channel need to be owned by the contract

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `channel`   | string      |          |  |


## cosmwasm/wasm/v1/proposal.proto

### StoreCodeProposal

StoreCodeProposal gov proposal content type to submit WASM code to the system

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `title`   | string      |          | Title is a short summary |
| `description`   | string      |          | Description is a human readable text |
| `run_as`   | string      |          | RunAs is the address that is passed to the contract's environment as sender |
| `wasm_byte_code`   | bytes      |          | WASMByteCode can be raw or gzip compressed|


### InstantiateContractProposal

InstantiateContractProposal gov proposal content type to instantiate a contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `title`   | string      |          | Title is a short summary |
| `description`   | string      |          | Description is a human readable text |
| `run_as`   | string      |          | RunAs is the address that is passed to the contract's environment as sender |
| `admin`   | string      |          | Admin is an optional address that can execute migrations|
| `code_id`   | uint64      |          | CodeID is the reference to the stored WASM code|
| `label`   | string      |          | Label is optional metadata to be stored with a constract instance.|
| `msg`   | bytes      |          | Msg json encoded message to be passed to the contract on instantiation|
| `funds`   | [Coin](base.md#Coin)       |   repeated       |  Funds coins that are transferred to the contract on instantiation|

### MigrateContractProposal

MigrateContractProposal gov proposal content type to migrate a contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `title`   | string      |          | Title is a short summary |
| `description`   | string      |          | Description is a human readable text |
| `contract`   | string      |          | Contract is the address of the smart contract |
| `code_id`   | uint64      |          | CodeID is the reference to the stored WASM code|
| `msg`   | bytes      |          |  Msg json encoded message to be passed to the contract on migration|

### SudoContractProposal

SudoContractProposal gov proposal content type to call sudo on a contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `title`   | string      |          | Title is a short summary |
| `description`   | string      |          | Description is a human readable text |
| `contract`   | string      |          | Contract is the address of the smart contract |
| `msg`   | bytes      |          |  Msg json encoded message to be passed to the contract as sudo|


### ExecuteContractProposal

ExecuteContractProposal gov proposal content type to call execute on a contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `title`   | string      |          | Title is a short summary |
| `description`   | string      |          | Description is a human readable text |
| `run_as`   | string      |          |RunAs is the address that is passed to the contract's environment as sender |
| `contract`   | string      |          | Contract is the address of the smart contract |
| `msg`   | bytes      |          |  Msg json encoded message to be passed to the contract as execute|
| `funds`   | [Coin](base.md#Coin)      |       repeated   |  Funds coins that are transferred to the contract on instantiation|

### UpdateAdminProposal

UpdateAdminProposal gov proposal content type to set an admin for a contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `title`   | string      |          | Title is a short summary |
| `description`   | string      |          | Description is a human readable text |
| `new_admin`   | string      |          |  NewAdmin address to be set|
| `contract`   | string      |          | Contract is the address of the smart contract |

### ClearAdminProposal

ClearAdminProposal gov proposal content type to clear the admin of a contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `title`   | string      |          | Title is a short summary |
| `description`   | string      |          | Description is a human readable text |
| `contract`   | string      |          | Contract is the address of the smart contract |


### PinCodesProposal

PinCodesProposal gov proposal content type to pin a set of code ids in the wasmvm cache.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `title`   | string      |          | Title is a short summary |
| `description`   | string      |          | Description is a human readable text |
| `code_ids`   | uint64      |    repeated      | CodeIDs references the new WASM codes |


### UnpinCodesProposal

UnpinCodesProposal gov proposal content type to unpin a set of code ids in the wasmvm cache.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `title`   | string      |          | Title is a short summary |
| `description`   | string      |          | Description is a human readable text |
| `code_ids`   | uint64      |    repeated      | CodeIDs references the new WASM codes |


### AccessConfigUpdate

AccessConfigUpdate contains the code id and the access config to be applied.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_id`   | uint64      |          | CodeID is the reference to the stored WASM code to be updated |
| `instantiate_permission`   | [AccessConfig](wasm.md#AccessConfig)      |          | InstantiatePermission to apply to the set of code ids |

### UpdateInstantiateConfigProposal

UpdateInstantiateConfigProposal gov proposal content type to update instantiate config to a  set of code ids.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `title`   | string      |          | Title is a short summary |
| `description`   | string      |          | Description is a human readable text |
| `access_config_updates`   | [AccessConfigUpdate](wasm.md#AccessConfigUpdate)      |    repeated      |AccessConfigUpdate contains the list of code ids and the access config to be applied. |


## cosmwasm/wasm/v1/query.proto

### QueryContractInfoRequest

QueryContractInfoRequest is the request type for the Query/ContractInfo RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `address`   | string      |          | address is the address of the contract to query |


### QueryContractInfoResponse

QueryContractInfoResponse is the response type for the Query/ContractInfo RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `address`   | string      |          | address is the address of the contract |
| `contract_info`   | [ContractInfo](wasm.md#ContractInfo)      |          | address is the address of the contract |

### QueryContractHistoryRequest

QueryContractHistoryRequest is the request type for the Query/ContractHistory RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `address`   | string      |          | address is the address of the contract to query |
| `pagination`   | [PageRequest](base.md#PageRequest)      |          | pagination defines an optional pagination for the request. |

### QueryContractHistoryResponse

QueryContractHistoryResponse is the request type for the Query/ContractHistory RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `entries`   | [ContractCodeHistoryEntry](wasm.md#ContractCodeHistoryEntry)      |          | |
| `pagination`   | [PageRequest](base.md#PageRequest)      |          | pagination defines an optional pagination for the request. |


### QueryContractsByCodeRequest

QueryContractsByCodeRequest is the request type for the Query/ContractsByCode RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_id`   | uint64      |          | grpc-gateway_out does not support Go style CodID|
| `pagination`   | [PageRequest](base.md#PageRequest)      |          | pagination defines an optional pagination for the request. |

### QueryContractsByCodeResponse

QueryContractsByCodeResponse is the request type for the Query/ContractsByCode RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `contracts`   | string      |  repeated        | contracts are a set of contract addresses|
| `pagination`   | [PageRequest](base.md#PageRequest)      |          | pagination defines an optional pagination for the request. |


### QueryAllContractStateRequest

QueryAllContractStateRequest is the request type for the Query/AllContractState RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `address`   | string      |          | address is the address of the contract|
| `pagination`   | [PageRequest](base.md#PageRequest)      |          | pagination defines an optional pagination for the request. |

### QueryAllContractStateResponse

QueryAllContractStateResponse is the request type for the Query/AllContractState RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `models`   | [Model](wasm.md#Model)      |  repeated        | |
| `pagination`   | [PageRequest](base.md#PageRequest)      |          | pagination defines an optional pagination for the request. |

### QueryRawContractStateRequest

QueryRawContractStateRequest is the request type for the Query/RawContractState RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `address`   | string     |          | address is the address of the contract|
| `query_data`   |bytes     |          |  |


### QueryRawContractStateResponse

QueryRawContractStateResponse is the request type for the Query/RawContractState RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `data`   |bytes     |          | Data contains the raw store data |


### QuerySmartContractStateRequest

QuerySmartContractStateRequest is the request type for the Query/SmartContractState RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `address`   | string     |          | address is the address of the contract|
| `query_data`   |bytes     |          | QueryData contains the query data passed to the contract |


### QuerySmartContractStateResponse

QuerySmartContractStateResponse is the request type for the Query/SmartContractState RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `data`   |bytes     |          | Data contains the json data returned from the smart contract |

### QueryCodeRequest

QueryCodeRequest is the request type for the Query/Code RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_id`   | uint64     |          | grpc-gateway_out does not support Go style CodID|


### QueryCodeResponse

QueryCodeResponse is the response type for the Query/Code RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_info`   | [CodeInfoResponse](wasm.md#CodeInfoResponse)     |          | grpc-gateway_out does not support Go style CodID|
| `data`   |bytes     |          |  |


### CodeInfoResponse

CodeInfoResponse contains code meta data from CodeInfo

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_id`   | uint64     |          | id for legacy support|
| `creator`   | string     |          | id for legacy support|
| `data_hash`   | bytes     |          | id for legacy support|

### QueryCodesRequest

QueryCodesRequest is the request type for the Query/Codes RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `pagination`   | [PageRequest](base.md#PageRequest)    |          | pagination defines an optional pagination for the request.|


### QueryCodesResponse

QueryCodesResponse is the response type for the Query/Codes RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_infos`   | [CodeInfoResponse](wasm.md#CodeInfoResponse)     |          | pagination defines an optional pagination for the request.|
| `pagination`   | [PageRequest](base.md#PageRequest)     |          | pagination defines an optional pagination for the request.|


### QueryPinnedCodesRequest

QueryPinnedCodesRequest is the request type for the Query/PinnedCodes RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `pagination`   | [PageRequest](base.md#PageRequest)     |          | pagination defines an optional pagination for the request.|

### QueryPinnedCodesResponse

QueryPinnedCodesResponse is the request type for the Query/PinnedCodes RPC method

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_ids`   | uint64   |  repeated        | pagination defines an optional pagination for the request.|
| `pagination`   | [PageRequest](base.md#PageRequest)     |          | pagination defines an optional pagination for the request.|

### Query

Query defines the gRPC querier service.

| Method Name                     | Request Type                                                                                                                | Response Type                                                                                                                 | Description                                                                                   | HTTP Verb | Endpoint                                                                                                 |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------- | -------------------------------------------------------------------------------------------------------- |
| `ContractInfo`                  | [QueryContractInfoRequest](wasm.md#QueryContractInfoRequest)                                                                | [QueryContractInfoResponse](wasm.md#QueryContractInfoResponse)                                                                | ContractInfo gets the contract meta data                                                      | GET       | /cosmwasm/wasm/v1/contract/{address}                                                                     |
| `ContractHistory`               | [QueryContractHistoryRequest](wasm.md#QueryContractHistoryRequest)                                                          | [QueryContractHistoryResponse](wasm.md#QueryContractHistoryResponse)                                                          |  ContractHistory gets the contract code history                                               | GET       | /cosmwasm/wasm/v1/contract/{address}/history                                                             |
| `ContractsByCode`               | [QueryContractsByCodeRequest](wasm.md#QueryContractsByCodeRequest)                                                          | [QueryContractsByCodeResponse](wasm.md#QueryContractsByCodeResponse)                                                          | ContractsByCode lists all smart contracts for a code id                                       | GET       | /cosmwasm/wasm/v1/code/{code_id}/contracts                                                               |
| `AllContractState`              | [QueryAllContractStateRequest](wasm.md#QueryAllContractStateRequest)                                                        | [QueryAllContractStateResponse](wasm.md#QueryAllContractStateResponse)                                                        | AllContractState gets all raw store data for a single contract.                               | GET       | /cosmwasm/wasm/v1/contract/{address}/state                                                               |
| `RawContractState`              | [QueryRawContractStateRequest](wasm.md#QueryRawContractStateRequest)                                                        | [QueryRawContractStateResponse](wasm.md#QueryRawContractStateResponse)                                                        | RawContractState gets single key from the raw store data of a contract                        | GET       | /cosmwasm/wasm/v1/contract/{address}/raw/{query_data}                                                    |
| `SmartContractState`            | [QuerySmartContractStateRequest](wasm.md#QuerySmartContractStateRequest)                                                    | [QuerySmartContractStateResponse](wasm.md#QuerySmartContractStateResponse)                                                    | SmartContractState get smart query result from the contract.                                  | GET       | /cosmwasm/wasm/v1/contract/{address}/smart/{query_data}                                                  |
| `Code`                          | [QueryCodeRequest](wasm.md#QueryCodeRequest)                                                                                | [QueryCodeResponse](wasm.md#QueryCodeResponse)                                                                                |  Code gets the binary code and metadata for a singe wasm code.                                | GET       | /cosmwasm/wasm/v1/code/{code_id}                                                                         |
| `Codes`                         | [QueryCodesRequest](wasm.md#QueryCodesRequest)                                                                              | [QueryCodesResponse](wasm.md#QueryCodesResponse)                                                                              | Codes gets the metadata for all stored wasm codes.                                            | GET       | /cosmwasm/wasm/v1/code                                                                                   |
| `PinnedCodes`                   | [QueryPinnedCodesRequest](wasm.md#QueryPinnedCodesRequest)                                                                  | [QueryPinnedCodesResponse](wasm.md#QueryPinnedCodesResponse)                                                                  | PinnedCodes gets the pinned code ids.                                                         | GET       | //cosmwasm/wasm/v1/codes/pinned                                                                          |


## cosmwasm/wasm/v1/tx.proto

### MsgStoreCode

MsgStoreCode submit Wasm code to the system

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `sender`   | string   |          | Sender is the that actor that signed the messages.|
| `wasm_byte_code`   | bytes     |          | WASMByteCode can be raw or gzip compressed.|
| `instantiate_permission`   | [AccessConfig](wasm.md#AccessConfig)     |          | InstantiatePermission access control to apply on contract creation,optional.|


### MsgStoreCodeResponse

MsgStoreCodeResponse returns store result data.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_id`   | uint64   |          | CodeID is the reference to the stored WASM code.|


### MsgInstantiateContract

MsgInstantiateContract create a new smart contract instance for the given code id.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `sender`   | string   |          | Sender is the that actor that signed the messages.|
| `admin`   | string   |          | Admin is an optional address that can execute migrations.|
| `code_id`   | uint64   |          | CodeID is the reference to the stored WASM code.|
| `label`   | string   |          | Label is optional metadata to be stored with a contract instance.|
| `msg`   | bytes   |          | Msg json encoded message to be passed to the contract on instantiation.|
| `funds`   | [Coin](base.md#Coin)   |   repeated       | Funds coins that are transferred to the contract on instantiation.|

### MsgInstantiateContractResponse

MsgInstantiateContractResponse return instantiation result data.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `address`   | string   |          | Address is the bech32 address of the new contract instance.|
| `data`   | bytes   |          | Data contains base64-encoded bytes to returned from the contract.|

### MsgExecuteContract

MsgExecuteContract submits the given message data to a smart contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `sender`   | string   |          | Sender is the that actor that signed the messages.|
| `contract`   | string   |          | Contract is the address of the smart contract.|
| `msg`   | bytes   |          | Msg json encoded message to be passed to the contract.|
| `funds`   | [Coin](base.md#Coin)    |   repeated       | Funds coins that are transferred to the contract on execution.|

### MsgExecuteContractResponse

MsgExecuteContractResponse returns execution result data.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `data`   | bytes   |          | Data contains base64-encoded bytes to returned from the contract.|


### MsgMigrateContract

MsgMigrateContract runs a code upgrade/ downgrade for a smart contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `sender`   | string   |          | Sender is the that actor that signed the messages.|
| `contract`   | string   |          | Contract is the address of the smart contract.|
| `code_id`   | string   |          | CodeID references the new WASM code.|
| `msg`   | uint64   |          | Msg json encoded message to be passed to the contract on migration.|

### MsgMigrateContractResponse

MsgMigrateContractResponse returns contract migration result data.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `data`   | bytes   |          | Data contains same raw bytes returned as data from the wasm contract(May be empty).|

### MsgUpdateAdmin

MsgUpdateAdmin sets a new admin for a smart contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `sender`   | string   |          | Sender is the that actor that signed the messages.|
| `new_admin`   | string   |          |NewAdmin address to be set.|
| `contract`   | string   |          | Contract is the address of the smart contract.|

### MsgUpdateAdminResponse

MsgUpdateAdminResponse returns empty data.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |

### MsgClearAdmin

MsgClearAdmin removes any admin stored for a smart contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `sender`   | string   |          | Sender is the that actor that signed the messages.|
| `contract`   | string   |          | Contract is the address of the smart contract.|

### MsgClearAdminResponse

MsgClearAdminResponse returns empty data.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |


### Msg

Msg defines the wasm Msg service.

| Method Name       | Request Type                                                                  | Response Type                                                                                 | Description                                                                                                                               | HTTP Verb | Endpoint |
| ----------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | --------- | -------- |
| `StoreCode`               | [MsgStoreCode](wasm.md#MsgStoreCode)                               | [MsgStoreCodeResponse](wasm.md#MsgStoreCodeResponse)                                       | StoreCode to submit Wasm code to the system.                                                                                              |           |          |
| `InstantiateContract`     | [MsgInstantiateContract](wasm.md#MsgInstantiateContract)           | [MsgInstantiateContractResponse](wasm.md#MsgInstantiateContractResponse)                   | Instantiate creates a new smart contract instance for the given code id.                                                                  |           |          |
| `ExecuteContract`         | [MsgExecuteContract](wasm.md#MsgExecuteContract)                   | [MsgExecuteContractResponse](wasm.md#MsgExecuteContractResponse)                           | Execute submits the given message data to a smart contract.                                                                               |           |          |
| `MigrateContract`         | [MsgMigrateContract](wasm.md#MsgMigrateContract)                   | [MsgMigrateContractResponse](wasm.md#MsgMigrateContractResponse)                           | Migrate runs a code upgrade downgrade for a smart contract.                                                                               |           |          |
| `UpdateAdmin`             | [MsgUpdateAdmin](wasm.md#MsgUpdateAdmin)                           | [MsgUpdateAdminResponse](wasm.md#MsgUpdateAdminResponse)                                   | UpdateAdmin sets a new   admin for a smart contract.                                                                                      |           |          |
| `ClearAdmin`              | [MsgClearAdmin](wasm.md#MsgClearAdmin)                             | [MsgClearAdminResponse](wasm.md#MsgClearAdminResponse)                                     | ClearAdmin removes any admin stored for a smart contract.                                                                                 |           |          |



## cosmwasm/wasm/v1/tx.proto


### AccessType

AccessType permission types.

| Name                      | Number | Description                                      |
| ------------------------- | ------ | ------------------------------------------------ |
| ACCESS_TYPE_UNSPECIFIED | 0      | AccessTypeUnspecified placeholder for empty value. |
| ACCESS_TYPE_NOBODY    | 1      | AccessTypeNobody forbidden. |
| ACCESS_TYPE_ONLY_ADDRESS   | 2      | AccessTypeOnlyAddress restricted to an address. |
| ACCESS_TYPE_EVERYBODY      | 3      | AccessTypeEverybody unrestricted.       |

### AccessTypeParam

AccessTypeParam.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `value`   | [AccessType](wasm.md#AccessType)   |          | |



### AccessConfig

AccessConfig access control type.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `permission`   | [AccessType](wasm.md#AccessType)   |          | |
| `address`   | string   |          | |

### Params

Params defines the set of wasm parameters.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_upload_access`   | [AccessConfig](wasm.md#AccessType)   |          | |
| `instantiate_default_permission`   | [AccessType](wasm.md#AccessType)   |          | |

### CodeInfo

CodeInfo is data for the uploaded contract WASM code.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_hash`   | bytes   |          | CodeHash is the unique identifier created by wasmvm.|
| `creator`   | string  |          |Creator address who initially stored the code. |
| `instantiate_config`   | [AccessConfig](wasm.md#AccessConfig)  |          |InstantiateConfig access control to apply on contract creation, optional. |

### ContractInfo

ContractInfo stores a WASM contract instance.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `code_id`   | uint64   |          | CodeID is the reference to the stored Wasm code.|
| `creator`   | string  |          |Creator address who initially instantiated the contract. |
| `admin`   | string  |          |Admin is an optional address that can execute migrations. |
| `label`   | string  |          |Label is optional metadata to be stored with a contract instance. |
| `created`   | [AbsoluteTxPosition](wasm.md#AbsoluteTxPosition)  |          |Created Tx position when the contract was instantiated. This data should kept internal and not be exposed via query results. Just use for sorting. |
| `ibc_port_id`   | string  |          | |
| `extension`   | [Any]  |          |Extension is an extension point to store custom metadata within the persistence model. |


### ContractCodeHistoryOperationType

ContractCodeHistoryOperationType actions that caused a code change.

| Name                      | Number | Description                                      |
| ------------------------- | ------ | ------------------------------------------------ |
| CONTRACT_CODE_HISTORY_OPERATION_TYPE_UNSPECIFIED | 0      |  ContractCodeHistoryOperationTypeUnspecified placeholder for empty value. |
| CONTRACT_CODE_HISTORY_OPERATION_TYPE_INIT    | 1      | ContractCodeHistoryOperationTypeInit on chain contract instantiation. |
| CONTRACT_CODE_HISTORY_OPERATION_TYPE_MIGRATE   | 2      | ContractCodeHistoryOperationTypeMigrate code migration. |
| CONTRACT_CODE_HISTORY_OPERATION_TYPE_GENESIS      | 3      | ContractCodeHistoryOperationTypeGenesis based on genesis data.       |

### ContractCodeHistoryEntry

ContractCodeHistoryEntry metadata to a contract.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `operation`   | [ContractCodeHistoryOperationType](wasm.md#ContractCodeHistoryOperationType)   |          | |
| `code_id`   | uint64  |          |CodeID is the reference to the stored WASM code. |
| `updated`   | [AbsoluteTxPosition](wasm.md#AbsoluteTxPosition)  |          |Updated Tx position when the operation was executed. |
| `msg`   | bytes  |          |CodeID is the reference to the stored WASM code. |

### AbsoluteTxPosition

AbsoluteTxPosition is a unique transaction position that allows for global ordering of transactions.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `block_height`   | uint64  |          | BlockHeight is the block the contract was created at.|
| `tx_index`   | uint64  |          |TxIndex is a monotonic counter within the block (actual transaction index, or gas consumed). |

### Model

Model is a struct that holds a KV pair.

| Field      | Type                                                     | Label    | Description                                      |
| ---------- | -------------------------------------------------------- | -------- | ------------------------------------------------ |
| `key`   | bytes  |          | hex-encode key to read it better (this is often ascii).|
| `value`   | bytes  |          |base64-encode raw value. |















