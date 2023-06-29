## cosmos/params/v1beta1/params.proto

### ParamChange

ParamChange defines an individual parameter change, for use in ParameterChangeProposal.

| Field      | Type                           | Label | Description |
| ---------- | ------------------------------ | ----- | ----------- |
| `subspace` | [string](value.md#string) |       |             |
| `key`      | [string](value.md#string) |       |             |
| `value`    | [string](value.md#string) |       |             |

### ParameterChangeProposal

ParameterChangeProposal defines a proposal to change one or more parameters.

| Field         | Type                                                           | Label    | Description |
| ------------- | -------------------------------------------------------------- | -------- | ----------- |
| `title`       | [string](value.md#string)                                 |          |             |
| `description` | [string](value.md#string)                                 |          |             |
| `changes`     | [ParamChange](params.md#cosmos.params.v1beta1.ParamChange) | repeated |             |



## cosmos/params/v1beta1/query.proto

### QueryParamsRequest

QueryParamsRequest is request type for the Query/Params RPC method.

| Field      | Type                           | Label | Description                                             |
| ---------- | ------------------------------ | ----- | ------------------------------------------------------- |
| `subspace` | [string](value.md#string) |       | subspace defines the module to query the parameter for. |
| `key`      | [string](value.md#string) |       | key defines the key of the parameter in the subspace.   |

### QueryParamsResponse

QueryParamsResponse is response type for the Query/Params RPC method.

| Field   | Type                                                           | Label | Description                          |
| ------- | -------------------------------------------------------------- | ----- | ------------------------------------ |
| `param` | [ParamChange](params.md#cosmos.params.v1beta1.ParamChange) |       | param defines the queried parameter. |

### Query

Query defines the gRPC querier service.

| Method Name | Request Type                                                                 | Response Type                                                                  | Description                                                                  | HTTP Verb | Endpoint                      |
| ----------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | ---------------------------------------------------------------------------- | --------- | ----------------------------- |
| `Params`    | [QueryParamsRequest](params.md#cosmos.params.v1beta1.QueryParamsRequest) | [QueryParamsResponse](params.md#cosmos.params.v1beta1.QueryParamsResponse) | Params queries a specific parameter of a module, given its subspace and key. | GET       | /cosmos/params/v1beta1/params |

