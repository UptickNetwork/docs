## cosmos/evidence/v1beta1/evidence.proto

### Equivocation

Equivocation implements the Evidence interface and defines evidence of double signing misbehavior.

| Field               | Type                                                                 | Label | Description |
| ------------------- | -------------------------------------------------------------------- | ----- | ----------- |
| `height`            | [int64](value.md#int64)                                         |       |             |
| `time`              | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |       |             |
| `power`             | [int64](value.md#int64)                                         |       |             |
| `consensus_address` | [string](value.md#string)                                       |       |             |



## cosmos/evidence/v1beta1/genesis.proto

### GenesisState

GenesisState defines the evidence module's genesis state.

| Field      | Type                                                     | Label    | Description                                   |
| ---------- | -------------------------------------------------------- | -------- | --------------------------------------------- |
| `evidence` | google.protobuf.Any | repeated | evidence defines all the evidence at genesis. |



## cosmos/evidence/v1beta1/query.proto

### QueryAllEvidenceRequest

QueryEvidenceRequest is the request type for the Query/AllEvidence RPC method.

| Field        | Type                                                                                         | Label | Description                                                |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request. |

### QueryAllEvidenceResponse

QueryAllEvidenceResponse is the response type for the Query/AllEvidence RPC method.

| Field        | Type                                                                                           | Label    | Description                                        |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `evidence`   | google.protobuf.Any                                       | repeated | evidence returns all evidences.                    |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### QueryEvidenceRequest

QueryEvidenceRequest is the request type for the Query/Evidence RPC method.

| Field           | Type                         | Label | Description                                                |
| --------------- | ---------------------------- | ----- | ---------------------------------------------------------- |
| `evidence_hash` | [bytes](value.md#bytes) |       | evidence_hash defines the hash of the requested evidence. |

### QueryEvidenceResponse

QueryEvidenceResponse is the response type for the Query/Evidence RPC method.

| Field      | Type                                                     | Label | Description                              |
| ---------- | -------------------------------------------------------- | ----- | ---------------------------------------- |
| `evidence` | google.protobuf.Any |       | evidence returns the requested evidence. |

### Query

Query defines the gRPC querier service.

| Method Name   | Request Type                                                                             | Response Type                                                                              | Description                                       | HTTP Verb | Endpoint                                           |
| ------------- | ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------- | --------- | -------------------------------------------------- |
| `Evidence`    | [QueryEvidenceRequest](evidence.md#cosmos.evidence.v1beta1.QueryEvidenceRequest)       | [QueryEvidenceResponse](evidence.md#cosmos.evidence.v1beta1.QueryEvidenceResponse)       | Evidence queries evidence based on evidence hash. | GET       | /cosmos/evidence/v1beta1/evidence/{evidence_hash} |
| `AllEvidence` | [QueryAllEvidenceRequest](evidence.md#cosmos.evidence.v1beta1.QueryAllEvidenceRequest) | [QueryAllEvidenceResponse](evidence.md#cosmos.evidence.v1beta1.QueryAllEvidenceResponse) | AllEvidence queries all evidence.                 | GET       | /cosmos/evidence/v1beta1/evidence                  |



## cosmos/evidence/v1beta1/tx.proto

### MsgSubmitEvidence

MsgSubmitEvidence represents a message that supports submitting arbitrary Evidence of misbehavior such as equivocation or counterfactual signing.

| Field       | Type                                                     | Label | Description |
| ----------- | -------------------------------------------------------- | ----- | ----------- |
| `submitter` | [string](value.md#string)                           |       |             |
| `evidence`  | google.protobuf.Any |       |             |

### MsgSubmitEvidenceResponse

MsgSubmitEvidenceResponse defines the Msg/SubmitEvidence response type.

| Field  | Type                         | Label | Description                            |
| ------ | ---------------------------- | ----- | -------------------------------------- |
| `hash` | [bytes](value.md#bytes) |       | hash defines the hash of the evidence. |

### Msg

Msg defines the evidence Msg service.

| Method Name      | Request Type                                                                 | Response Type                                                                                | Description                                                                                                 | HTTP Verb | Endpoint |
| ---------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | --------- | -------- |
| `SubmitEvidence` | [MsgSubmitEvidence](evidence.md#cosmos.evidence.v1beta1.MsgSubmitEvidence) | [MsgSubmitEvidenceResponse](evidence.md#cosmos.evidence.v1beta1.MsgSubmitEvidenceResponse) | SubmitEvidence submits an arbitrary Evidence of misbehavior such as equivocation or counterfactual signing. |           |          |

