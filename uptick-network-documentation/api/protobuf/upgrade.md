## cosmos/upgrade/v1beta1/upgrade.proto

### CancelSoftwareUpgradeProposal

CancelSoftwareUpgradeProposal is a gov Content type for cancelling a software upgrade.

| Field         | Type                           | Label | Description |
| ------------- | ------------------------------ | ----- | ----------- |
| `title`       | [string](value.md#string) |       |             |
| `description` | [string](value.md#string) |       |             |

### Plan

Plan specifies information about a planned upgrade and when it should occur.

| Field                   | Type                                                                 | Label | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ----------------------- | -------------------------------------------------------------------- | ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`                  | [string](value.md#string)                                       |       | Sets the name for the upgrade. This name will be used by the upgraded version of the software to apply any special "on-upgrade" commands during the first BeginBlock method after the upgrade is applied. It is also used to detect whether a software version can handle a given upgrade. If no upgrade handler with this name has been set in the software, it will be assumed that the software is out-of-date when the upgrade Time or Height is reached and the software will exit. |
| `time`                  | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |       | The time after which the upgrade must be performed. Leave set to its zero value to use a pre-defined Height instead.                                                                                                                                                                                                                                                                                                                                                                     |
| `height`                | [int64](value.md#int64)                                         |       | The height at which the upgrade must be performed. Only used if Time is not set.                                                                                                                                                                                                                                                                                                                                                                                                         |
| `info`                  | [string](value.md#string)                                       |       | Any application specific upgrade info to be included on-chain such as a git commit that validators could automatically upgrade to                                                                                                                                                                                                                                                                                                                                                        |
| `upgraded_client_state` | google.protobuf.Any             |       | IBC-enabled chains can opt-in to including the upgraded client state in its upgrade plan This will make the chain commit to the correct upgraded (self) client state before the upgrade occurs, so that connecting chains can verify that the new upgraded client is valid by verifying a proof on the previous version of the chain. This will allow IBC connections to persist smoothly across planned chain upgrades                                                                  |

### SoftwareUpgradeProposal

SoftwareUpgradeProposal is a gov Content type for initiating a software upgrade.

| Field         | Type                                              | Label | Description |
| ------------- | ------------------------------------------------- | ----- | ----------- |
| `title`       | [string](value.md#string)                    |       |             |
| `description` | [string](value.md#string)                    |       |             |
| `plan`        | [Plan](upgrade.md#cosmos.upgrade.v1beta1.Plan) |       |             |

## cosmos/upgrade/v1beta1/query.proto

### QueryAppliedPlanRequest

QueryCurrentPlanRequest is the request type for the Query/AppliedPlan RPC method.

| Field  | Type                           | Label | Description                                        |
| ------ | ------------------------------ | ----- | -------------------------------------------------- |
| `name` | [string](value.md#string) |       | name is the name of the applied plan to query for. |

### QueryAppliedPlanResponse

QueryAppliedPlanResponse is the response type for the Query/AppliedPlan RPC method.

| Field    | Type                         | Label | Description                                               |
| -------- | ---------------------------- | ----- | --------------------------------------------------------- |
| `height` | [int64](value.md#int64) |       | height is the block height at which the plan was applied. |

### QueryCurrentPlanRequest

QueryCurrentPlanRequest is the request type for the Query/CurrentPlan RPC method.

### QueryCurrentPlanResponse

QueryCurrentPlanResponse is the response type for the Query/CurrentPlan RPC method.

| Field  | Type                                              | Label | Description                       |
| ------ | ------------------------------------------------- | ----- | --------------------------------- |
| `plan` | [Plan](upgrade.md#cosmos.upgrade.v1beta1.Plan) |       | plan is the current upgrade plan. |

### QueryUpgradedConsensusStateRequest

QueryUpgradedConsensusStateRequest is the request type for the Query/UpgradedConsensusState RPC method.

| Field         | Type                         | Label | Description                                                                                                               |
| ------------- | ---------------------------- | ----- | ------------------------------------------------------------------------------------------------------------------------- |
| `last_height` | [int64](value.md#int64) |       | last height of the current chain must be sent in request as this is the height under which next consensus state is stored |

### QueryUpgradedConsensusStateResponse

QueryUpgradedConsensusStateResponse is the response type for the Query/UpgradedConsensusState RPC method.

| Field                      | Type                                                     | Label | Description |
| -------------------------- | -------------------------------------------------------- | ----- | ----------- |
| `upgraded_consensus_state` | google.protobuf.Any |       |             |

### Query

Query defines the gRPC upgrade querier service.

| Method Name              | Request Type                                                                                                  | Response Type                                                                                                   | Description                                                                                                                                                                                                                                      | HTTP Verb | Endpoint                                                          |
| ------------------------ | ------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------- | ----------------------------------------------------------------- |
| `CurrentPlan`            | [QueryCurrentPlanRequest](upgrade.md#cosmos.upgrade.v1beta1.QueryCurrentPlanRequest)                       | [QueryCurrentPlanResponse](upgrade.md#cosmos.upgrade.v1beta1.QueryCurrentPlanResponse)                       | CurrentPlan queries the current upgrade plan.                                                                                                                                                                                                    | GET       | /cosmos/upgrade/v1beta1/current_plan                             |
| `AppliedPlan`            | [QueryAppliedPlanRequest](upgrade.md#cosmos.upgrade.v1beta1.QueryAppliedPlanRequest)                       | [QueryAppliedPlanResponse](upgrade.md#cosmos.upgrade.v1beta1.QueryAppliedPlanResponse)                       | AppliedPlan queries a previously applied upgrade plan by its name.                                                                                                                                                                               | GET       | /cosmos/upgrade/v1beta1/applied_plan/{name}                      |
| `UpgradedConsensusState` | [QueryUpgradedConsensusStateRequest](upgrade.md#cosmos.upgrade.v1beta1.QueryUpgradedConsensusStateRequest) | [QueryUpgradedConsensusStateResponse](upgrade.md#cosmos.upgrade.v1beta1.QueryUpgradedConsensusStateResponse) | UpgradedConsensusState queries the consensus state that will serve as a trusted kernel for the next version of this chain. It will only be stored at the last height of this chain. UpgradedConsensusState RPC not supported with legacy querier | GET       | /cosmos/upgrade/v1beta1/upgraded_consensus_state/{last_height} |

