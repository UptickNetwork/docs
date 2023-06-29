## cosmos/distribution/v1beta1/distribution.proto

### CommunityPoolSpendProposal

CommunityPoolSpendProposal details a proposal for use of community funds, together with how many coins are proposed to be spent, and to which recipient account.

| Field         | Type                                                               | Label    | Description |
| ------------- | ------------------------------------------------------------------ | -------- | ----------- |
| `title`       | [string](value.md#string)                                     |          |             |
| `description` | [string](value.md#string)                                     |          |             |
| `recipient`   | [string](value.md#string)                                     |          |             |
| `amount`      | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |

### CommunityPoolSpendProposalWithDeposit

CommunityPoolSpendProposalWithDeposit defines a CommunityPoolSpendProposal with a deposit

| Field         | Type                           | Label | Description |
| ------------- | ------------------------------ | ----- | ----------- |
| `title`       | [string](value.md#string) |       |             |
| `description` | [string](value.md#string) |       |             |
| `recipient`   | [string](value.md#string) |       |             |
| `amount`      | [string](value.md#string) |       |             |
| `deposit`     | [string](value.md#string) |       |             |

### DelegationDelegatorReward

DelegationDelegatorReward represents the properties of a delegator's delegation reward.

| Field               | Type                                                                     | Label    | Description |
| ------------------- | ------------------------------------------------------------------------ | -------- | ----------- |
| `validator_address` | [string](value.md#string)                                           |          |             |
| `reward`            | [cosmos.base.v1beta1.DecCoin](base.md#cosmos.base.v1beta1.DecCoin) | repeated |             |

### DelegatorStartingInfo

DelegatorStartingInfo represents the starting info for a delegator reward period. It tracks the previous validator period, the delegation's amount of staking token, and the creation height (to check later on if any slashes have occurred). NOTE: Even though validators are slashed to whole staking tokens, the delegators within the validator may be left with less than a full token, thus sdk.Dec is used.

| Field             | Type                           | Label | Description |
| ----------------- | ------------------------------ | ----- | ----------- |
| `previous_period` | [uint64](value.md#uint64) |       |             |
| `stake`           | [string](value.md#string) |       |             |
| `height`          | [uint64](value.md#uint64) |       |             |

### FeePool

FeePool is the global fee pool for distribution.

| Field            | Type                                                                     | Label    | Description |
| ---------------- | ------------------------------------------------------------------------ | -------- | ----------- |
| `community_pool` | [cosmos.base.v1beta1.DecCoin](base.md#cosmos.base.v1beta1.DecCoin) | repeated |             |

### Params

Params defines the set of params for the distribution module.

| Field                   | Type                           | Label | Description |
| ----------------------- | ------------------------------ | ----- | ----------- |
| `community_tax`         | [string](value.md#string) |       |             |
| `base_proposer_reward`  | [string](value.md#string) |       |             |
| `bonus_proposer_reward` | [string](value.md#string) |       |             |
| `withdraw_addr_enabled` | [bool](value.md#bool)     |       |             |

### ValidatorAccumulatedCommission

ValidatorAccumulatedCommission represents accumulated commission for a validator kept as a running counter, can be withdrawn at any time.

| Field        | Type                                                                     | Label    | Description |
| ------------ | ------------------------------------------------------------------------ | -------- | ----------- |
| `commission` | [cosmos.base.v1beta1.DecCoin](base.md#cosmos.base.v1beta1.DecCoin) | repeated |             |

### ValidatorCurrentRewards

ValidatorCurrentRewards represents current rewards and current period for a validator kept as a running counter and incremented each block as long as the validator's tokens remain constant.

| Field     | Type                                                                     | Label    | Description |
| --------- | ------------------------------------------------------------------------ | -------- | ----------- |
| `rewards` | [cosmos.base.v1beta1.DecCoin](base.md#cosmos.base.v1beta1.DecCoin) | repeated |             |
| `period`  | [uint64](value.md#uint64)                                           |          |             |

### ValidatorHistoricalRewards

ValidatorHistoricalRewards represents historical rewards for a validator. Height is implicit within the store key. Cumulative reward ratio is the sum from the zeroeth period until this period of rewards / tokens, per the spec. The reference count indicates the number of objects which might need to reference this historical entry at any point. ReferenceCount = number of outstanding delegations which ended the associated period (and might need to read that record)

* number of slashes which ended the associated period (and might need to read that record)
* one per validator for the zeroeth period, set on initialization

| Field                     | Type                                                                     | Label    | Description |
| ------------------------- | ------------------------------------------------------------------------ | -------- | ----------- |
| `cumulative_reward_ratio` | [cosmos.base.v1beta1.DecCoin](base.md#cosmos.base.v1beta1.DecCoin) | repeated |             |
| `reference_count`         | [uint32](value.md#uint32)                                           |          |             |

### ValidatorOutstandingRewards

ValidatorOutstandingRewards represents outstanding (un-withdrawn) rewards for a validator inexpensive to track, allows simple sanity checks.

| Field     | Type                                                                     | Label    | Description |
| --------- | ------------------------------------------------------------------------ | -------- | ----------- |
| `rewards` | [cosmos.base.v1beta1.DecCoin](base.md#cosmos.base.v1beta1.DecCoin) | repeated |             |

### ValidatorSlashEvent

ValidatorSlashEvent represents a validator slash event. Height is implicit within the store key. This is needed to calculate appropriate amount of staking tokens for delegations which are withdrawn after a slash has occurred.

| Field              | Type                           | Label | Description |
| ------------------ | ------------------------------ | ----- | ----------- |
| `validator_period` | [uint64](value.md#uint64) |       |             |
| `fraction`         | [string](value.md#string) |       |             |

### ValidatorSlashEvents

ValidatorSlashEvents is a collection of ValidatorSlashEvent messages.

| Field                    | Type                                                                                 | Label    | Description |
| ------------------------ | ------------------------------------------------------------------------------------ | -------- | ----------- |
| `validator_slash_events` | [ValidatorSlashEvent](distribution.md#cosmos.distribution.v1beta1.ValidatorSlashEvent) | repeated |             |



## cosmos/distribution/v1beta1/genesis.proto

### DelegatorStartingInfoRecord

DelegatorStartingInfoRecord used for import / export via genesis json.

| Field               | Type                                                                                     | Label | Description                                              |
| ------------------- | ---------------------------------------------------------------------------------------- | ----- | -------------------------------------------------------- |
| `delegator_address` | [string](value.md#string)                                                           |       | delegator_address is the address of the delegator.      |
| `validator_address` | [string](value.md#string)                                                           |       | validator_address is the address of the validator.      |
| `starting_info`     | [DelegatorStartingInfo](distribution.md#cosmos.distribution.v1beta1.DelegatorStartingInfo) |       | starting_info defines the starting info of a delegator. |

### DelegatorWithdrawInfo

DelegatorWithdrawInfo is the address for where distributions rewards are withdrawn to by default this struct is only used at genesis to feed in default withdraw addresses.

| Field               | Type                           | Label | Description                                                             |
| ------------------- | ------------------------------ | ----- | ----------------------------------------------------------------------- |
| `delegator_address` | [string](value.md#string) |       | delegator_address is the address of the delegator.                     |
| `withdraw_address`  | [string](value.md#string) |       | withdraw_address is the address to withdraw the delegation rewards to. |

### GenesisState

GenesisState defines the distribution module's genesis state.

| Field                               | Type                                                                                                                   | Label    | Description                                                                |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------------------------------- |
| `params`                            | [Params](distribution.md#cosmos.distribution.v1beta1.Params)                                                             |          | params defines all the paramaters of the module.                           |
| `fee_pool`                          | [FeePool](distribution.md#cosmos.distribution.v1beta1.FeePool)                                                           |          | fee_pool defines the fee pool at genesis.                                 |
| `delegator_withdraw_infos`          | [DelegatorWithdrawInfo](distribution.md#cosmos.distribution.v1beta1.DelegatorWithdrawInfo)                               | repeated | fee_pool defines the delegator withdraw infos at genesis.                 |
| `previous_proposer`                 | [string](value.md#string)                                                                                         |          | fee_pool defines the previous proposer at genesis.                        |
| `outstanding_rewards`               | [ValidatorOutstandingRewardsRecord](distribution.md#cosmos.distribution.v1beta1.ValidatorOutstandingRewardsRecord)       | repeated | fee_pool defines the outstanding rewards of all validators at genesis.    |
| `validator_accumulated_commissions` | [ValidatorAccumulatedCommissionRecord](distribution.md#cosmos.distribution.v1beta1.ValidatorAccumulatedCommissionRecord) | repeated | fee_pool defines the accumulated commisions of all validators at genesis. |
| `validator_historical_rewards`      | [ValidatorHistoricalRewardsRecord](distribution.md#cosmos.distribution.v1beta1.ValidatorHistoricalRewardsRecord)         | repeated | fee_pool defines the historical rewards of all validators at genesis.     |
| `validator_current_rewards`         | [ValidatorCurrentRewardsRecord](distribution.md#cosmos.distribution.v1beta1.ValidatorCurrentRewardsRecord)               | repeated | fee_pool defines the current rewards of all validators at genesis.        |
| `delegator_starting_infos`          | [DelegatorStartingInfoRecord](distribution.md#cosmos.distribution.v1beta1.DelegatorStartingInfoRecord)                   | repeated | fee_pool defines the delegator starting infos at genesis.                 |
| `validator_slash_events`            | [ValidatorSlashEventRecord](distribution.md#cosmos.distribution.v1beta1.ValidatorSlashEventRecord)                       | repeated | fee_pool defines the validator slash events at genesis.                   |

### ValidatorAccumulatedCommissionRecord

ValidatorAccumulatedCommissionRecord is used for import / export via genesis json.

| Field               | Type                                                                                                       | Label | Description                                               |
| ------------------- | ---------------------------------------------------------------------------------------------------------- | ----- | --------------------------------------------------------- |
| `validator_address` | [string](value.md#string)                                                                             |       | validator_address is the address of the validator.       |
| `accumulated`       | [ValidatorAccumulatedCommission](distribution.md#cosmos.distribution.v1beta1.ValidatorAccumulatedCommission) |       | accumulated is the accumulated commission of a validator. |

### ValidatorCurrentRewardsRecord

ValidatorCurrentRewardsRecord is used for import / export via genesis json.

| Field               | Type                                                                                         | Label | Description                                         |
| ------------------- | -------------------------------------------------------------------------------------------- | ----- | --------------------------------------------------- |
| `validator_address` | [string](value.md#string)                                                               |       | validator_address is the address of the validator. |
| `rewards`           | [ValidatorCurrentRewards](distribution.md#cosmos.distribution.v1beta1.ValidatorCurrentRewards) |       | rewards defines the current rewards of a validator. |

### ValidatorHistoricalRewardsRecord

ValidatorHistoricalRewardsRecord is used for import / export via genesis json.

| Field               | Type                                                                                               | Label | Description                                                |
| ------------------- | -------------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `validator_address` | [string](value.md#string)                                                                     |       | validator_address is the address of the validator.        |
| `period`            | [uint64](value.md#uint64)                                                                     |       | period defines the period the historical rewards apply to. |
| `rewards`           | [ValidatorHistoricalRewards](distribution.md#cosmos.distribution.v1beta1.ValidatorHistoricalRewards) |       | rewards defines the historical rewards of a validator.     |

### ValidatorOutstandingRewardsRecord

ValidatorOutstandingRewardsRecord is used for import/export via genesis json.

| Field                 | Type                                                                     | Label    | Description                                                            |
| --------------------- | ------------------------------------------------------------------------ | -------- | ---------------------------------------------------------------------- |
| `validator_address`   | [string](value.md#string)                                           |          | validator_address is the address of the validator.                    |
| `outstanding_rewards` | [cosmos.base.v1beta1.DecCoin](base.md#cosmos.base.v1beta1.DecCoin) | repeated | outstanding_rewards represents the oustanding rewards of a validator. |

### ValidatorSlashEventRecord

ValidatorSlashEventRecord is used for import / export via genesis json.

| Field                   | Type                                                                                 | Label | Description                                                       |
| ----------------------- | ------------------------------------------------------------------------------------ | ----- | ----------------------------------------------------------------- |
| `validator_address`     | [string](value.md#string)                                                       |       | validator_address is the address of the validator.               |
| `height`                | [uint64](value.md#uint64)                                                       |       | height defines the block height at which the slash event occured. |
| `period`                | [uint64](value.md#uint64)                                                       |       | period is the period of the slash event.                          |
| `validator_slash_event` | [ValidatorSlashEvent](distribution.md#cosmos.distribution.v1beta1.ValidatorSlashEvent) |       | validator_slash_event describes the slash event.                |



## cosmos/distribution/v1beta1/query.proto

### QueryCommunityPoolRequest

QueryCommunityPoolRequest is the request type for the Query/CommunityPool RPC method.

### QueryCommunityPoolResponse

QueryCommunityPoolResponse is the response type for the Query/CommunityPool RPC method.

| Field  | Type                                                                     | Label    | Description                          |
| ------ | ------------------------------------------------------------------------ | -------- | ------------------------------------ |
| `pool` | [cosmos.base.v1beta1.DecCoin](base.md#cosmos.base.v1beta1.DecCoin) | repeated | pool defines community pool's coins. |

### QueryDelegationRewardsRequest

QueryDelegationRewardsRequest is the request type for the Query/DelegationRewards RPC method.

| Field               | Type                           | Label | Description                                                    |
| ------------------- | ------------------------------ | ----- | -------------------------------------------------------------- |
| `delegator_address` | [string](value.md#string) |       | delegator_address defines the delegator address to query for. |
| `validator_address` | [string](value.md#string) |       | validator_address defines the validator address to query for. |

### QueryDelegationRewardsResponse

QueryDelegationRewardsResponse is the response type for the Query/DelegationRewards RPC method.

| Field     | Type                                                                     | Label    | Description                                          |
| --------- | ------------------------------------------------------------------------ | -------- | ---------------------------------------------------- |
| `rewards` | [cosmos.base.v1beta1.DecCoin](base.md#cosmos.base.v1beta1.DecCoin) | repeated | rewards defines the rewards accrued by a delegation. |

### QueryDelegationTotalRewardsRequest

QueryDelegationTotalRewardsRequest is the request type for the Query/DelegationTotalRewards RPC method.

| Field               | Type                           | Label | Description                                                    |
| ------------------- | ------------------------------ | ----- | -------------------------------------------------------------- |
| `delegator_address` | [string](value.md#string) |       | delegator_address defines the delegator address to query for. |

### QueryDelegationTotalRewardsResponse

QueryDelegationTotalRewardsResponse is the response type for the Query/DelegationTotalRewards RPC method.

| Field     | Type                                                                                             | Label    | Description                                             |
| --------- | ------------------------------------------------------------------------------------------------ | -------- | ------------------------------------------------------- |
| `rewards` | [DelegationDelegatorReward](distribution.md#cosmos.distribution.v1beta1.DelegationDelegatorReward) | repeated | rewards defines all the rewards accrued by a delegator. |
| `total`   | [cosmos.base.v1beta1.DecCoin](base.md#cosmos.base.v1beta1.DecCoin)                         | repeated | total defines the sum of all the rewards.               |

### QueryDelegatorValidatorsRequest

QueryDelegatorValidatorsRequest is the request type for the Query/DelegatorValidators RPC method.

| Field               | Type                           | Label | Description                                                    |
| ------------------- | ------------------------------ | ----- | -------------------------------------------------------------- |
| `delegator_address` | [string](value.md#string) |       | delegator_address defines the delegator address to query for. |

### QueryDelegatorValidatorsResponse

QueryDelegatorValidatorsResponse is the response type for the Query/DelegatorValidators RPC method.

| Field        | Type                           | Label    | Description                                                      |
| ------------ | ------------------------------ | -------- | ---------------------------------------------------------------- |
| `validators` | [string](value.md#string) | repeated | validators defines the validators a delegator is delegating for. |

### QueryDelegatorWithdrawAddressRequest

QueryDelegatorWithdrawAddressRequest is the request type for the Query/DelegatorWithdrawAddress RPC method.

| Field               | Type                           | Label | Description                                                    |
| ------------------- | ------------------------------ | ----- | -------------------------------------------------------------- |
| `delegator_address` | [string](value.md#string) |       | delegator_address defines the delegator address to query for. |

### QueryDelegatorWithdrawAddressResponse

QueryDelegatorWithdrawAddressResponse is the response type for the Query/DelegatorWithdrawAddress RPC method.

| Field              | Type                           | Label | Description                                                   |
| ------------------ | ------------------------------ | ----- | ------------------------------------------------------------- |
| `withdraw_address` | [string](value.md#string) |       | withdraw_address defines the delegator address to query for. |

### QueryParamsRequest

QueryParamsRequest is the request type for the Query/Params RPC method.

### QueryParamsResponse

QueryParamsResponse is the response type for the Query/Params RPC method.

| Field    | Type                                                       | Label | Description                                  |
| -------- | ---------------------------------------------------------- | ----- | -------------------------------------------- |
| `params` | [Params](distribution.md#cosmos.distribution.v1beta1.Params) |       | params defines the parameters of the module. |

### QueryValidatorCommissionRequest

QueryValidatorCommissionRequest is the request type for the Query/ValidatorCommission RPC method

| Field               | Type                           | Label | Description                                                    |
| ------------------- | ------------------------------ | ----- | -------------------------------------------------------------- |
| `validator_address` | [string](value.md#string) |       | validator_address defines the validator address to query for. |

### QueryValidatorCommissionResponse

QueryValidatorCommissionResponse is the response type for the Query/ValidatorCommission RPC method

| Field        | Type                                                                                                       | Label | Description                                              |
| ------------ | ---------------------------------------------------------------------------------------------------------- | ----- | -------------------------------------------------------- |
| `commission` | [ValidatorAccumulatedCommission](distribution.md#cosmos.distribution.v1beta1.ValidatorAccumulatedCommission) |       | commission defines the commision the validator received. |

### QueryValidatorOutstandingRewardsRequest

QueryValidatorOutstandingRewardsRequest is the request type for the Query/ValidatorOutstandingRewards RPC method.

| Field               | Type                           | Label | Description                                                    |
| ------------------- | ------------------------------ | ----- | -------------------------------------------------------------- |
| `validator_address` | [string](value.md#string) |       | validator_address defines the validator address to query for. |

### QueryValidatorOutstandingRewardsResponse

QueryValidatorOutstandingRewardsResponse is the response type for the Query/ValidatorOutstandingRewards RPC method.

| Field     | Type                                                                                                 | Label | Description |
| --------- | ---------------------------------------------------------------------------------------------------- | ----- | ----------- |
| `rewards` | [ValidatorOutstandingRewards](distribution.md#cosmos.distribution.v1beta1.ValidatorOutstandingRewards) |       |             |

### QueryValidatorSlashesRequest

QueryValidatorSlashesRequest is the request type for the Query/ValidatorSlashes RPC method

| Field               | Type                                                                                         | Label | Description                                                                 |
| ------------------- | -------------------------------------------------------------------------------------------- | ----- | --------------------------------------------------------------------------- |
| `validator_address` | [string](value.md#string)                                                               |       | validator_address defines the validator address to query for.              |
| `starting_height`   | [uint64](value.md#uint64)                                                               |       | starting_height defines the optional starting height to query the slashes. |
| `ending_height`     | [uint64](value.md#uint64)                                                               |       | starting_height defines the optional ending height to query the slashes.   |
| `pagination`        | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request.                  |

### QueryValidatorSlashesResponse

QueryValidatorSlashesResponse is the response type for the Query/ValidatorSlashes RPC method.

| Field        | Type                                                                                           | Label    | Description                                         |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | --------------------------------------------------- |
| `slashes`    | [ValidatorSlashEvent](distribution.md#cosmos.distribution.v1beta1.ValidatorSlashEvent)           | repeated | slashes defines the slashes the validator received. |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response.  |

### Query

Query defines the gRPC querier service for distribution module.

| Method Name                   | Request Type                                                                                                                 | Response Type                                                                                                                  | Description                                                                   | HTTP Verb | Endpoint                                                                                  |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- | --------- | ----------------------------------------------------------------------------------------- |
| `Params`                      | [QueryParamsRequest](distribution.md#cosmos.distribution.v1beta1.QueryParamsRequest)                                           | [QueryParamsResponse](distribution.md#cosmos.distribution.v1beta1.QueryParamsResponse)                                           | Params queries params of the distribution module.                             | GET       | /cosmos/distribution/v1beta1/params                                                       |
| `ValidatorOutstandingRewards` | [QueryValidatorOutstandingRewardsRequest](distribution.md#cosmos.distribution.v1beta1.QueryValidatorOutstandingRewardsRequest) | [QueryValidatorOutstandingRewardsResponse](distribution.md#cosmos.distribution.v1beta1.QueryValidatorOutstandingRewardsResponse) | ValidatorOutstandingRewards queries rewards of a validator address.           | GET       | /cosmos/distribution/v1beta1/validators/{validator_address}/outstanding_rewards         |
| `ValidatorCommission`         | [QueryValidatorCommissionRequest](distribution.md#cosmos.distribution.v1beta1.QueryValidatorCommissionRequest)                 | [QueryValidatorCommissionResponse](distribution.md#cosmos.distribution.v1beta1.QueryValidatorCommissionResponse)                 | ValidatorCommission queries accumulated commission for a validator.           | GET       | /cosmos/distribution/v1beta1/validators/{validator_address}/commission                   |
| `ValidatorSlashes`            | [QueryValidatorSlashesRequest](distribution.md#cosmos.distribution.v1beta1.QueryValidatorSlashesRequest)                       | [QueryValidatorSlashesResponse](distribution.md#cosmos.distribution.v1beta1.QueryValidatorSlashesResponse)                       | ValidatorSlashes queries slash events of a validator.                         | GET       | /cosmos/distribution/v1beta1/validators/{validator_address}/slashes                      |
| `DelegationRewards`           | [QueryDelegationRewardsRequest](distribution.md#cosmos.distribution.v1beta1.QueryDelegationRewardsRequest)                     | [QueryDelegationRewardsResponse](distribution.md#cosmos.distribution.v1beta1.QueryDelegationRewardsResponse)                     | DelegationRewards queries the total rewards accrued by a delegation.          | GET       | /cosmos/distribution/v1beta1/delegators/{delegator_address}/rewards/{validator_address} |
| `DelegationTotalRewards`      | [QueryDelegationTotalRewardsRequest](distribution.md#cosmos.distribution.v1beta1.QueryDelegationTotalRewardsRequest)           | [QueryDelegationTotalRewardsResponse](distribution.md#cosmos.distribution.v1beta1.QueryDelegationTotalRewardsResponse)           | DelegationTotalRewards queries the total rewards accrued by a each validator. | GET       | /cosmos/distribution/v1beta1/delegators/{delegator_address}/rewards                      |
| `DelegatorValidators`         | [QueryDelegatorValidatorsRequest](distribution.md#cosmos.distribution.v1beta1.QueryDelegatorValidatorsRequest)                 | [QueryDelegatorValidatorsResponse](distribution.md#cosmos.distribution.v1beta1.QueryDelegatorValidatorsResponse)                 | DelegatorValidators queries the validators of a delegator.                    | GET       | /cosmos/distribution/v1beta1/delegators/{delegator_address}/validators                   |
| `DelegatorWithdrawAddress`    | [QueryDelegatorWithdrawAddressRequest](distribution.md#cosmos.distribution.v1beta1.QueryDelegatorWithdrawAddressRequest)       | [QueryDelegatorWithdrawAddressResponse](distribution.md#cosmos.distribution.v1beta1.QueryDelegatorWithdrawAddressResponse)       | DelegatorWithdrawAddress queries withdraw address of a delegator.             | GET       | /cosmos/distribution/v1beta1/delegators/{delegator_address}/withdraw_address            |
| `CommunityPool`               | [QueryCommunityPoolRequest](distribution.md#cosmos.distribution.v1beta1.QueryCommunityPoolRequest)                             | [QueryCommunityPoolResponse](distribution.md#cosmos.distribution.v1beta1.QueryCommunityPoolResponse)                             | CommunityPool queries the community pool coins.                               | GET       | /cosmos/distribution/v1beta1/community_pool                                              |



## cosmos/distribution/v1beta1/tx.proto

### MsgFundCommunityPool

MsgFundCommunityPool allows an account to directly fund the community pool.

| Field       | Type                                                               | Label    | Description |
| ----------- | ------------------------------------------------------------------ | -------- | ----------- |
| `amount`    | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |
| `depositor` | [string](value.md#string)                                     |          |             |

### MsgFundCommunityPoolResponse

MsgFundCommunityPoolResponse defines the Msg/FundCommunityPool response type.

### MsgSetWithdrawAddress

MsgSetWithdrawAddress sets the withdraw address for a delegator (or validator self-delegation).

| Field               | Type                           | Label | Description |
| ------------------- | ------------------------------ | ----- | ----------- |
| `delegator_address` | [string](value.md#string) |       |             |
| `withdraw_address`  | [string](value.md#string) |       |             |

### MsgSetWithdrawAddressResponse

MsgSetWithdrawAddressResponse defines the Msg/SetWithdrawAddress response type.

### MsgWithdrawDelegatorReward

MsgWithdrawDelegatorReward represents delegation withdrawal to a delegator from a single validator.

| Field               | Type                           | Label | Description |
| ------------------- | ------------------------------ | ----- | ----------- |
| `delegator_address` | [string](value.md#string) |       |             |
| `validator_address` | [string](value.md#string) |       |             |

### MsgWithdrawDelegatorRewardResponse

MsgWithdrawDelegatorRewardResponse defines the Msg/WithdrawDelegatorReward response type.

### MsgWithdrawValidatorCommission

MsgWithdrawValidatorCommission withdraws the full commission to the validator address.

| Field               | Type                           | Label | Description |
| ------------------- | ------------------------------ | ----- | ----------- |
| `validator_address` | [string](value.md#string) |       |             |

### MsgWithdrawValidatorCommissionResponse

MsgWithdrawValidatorCommissionResponse defines the Msg/WithdrawValidatorCommission response type.

### Msg

Msg defines the distribution Msg service.

| Method Name                   | Request Type                                                                                               | Response Type                                                                                                              | Description                                                                                                        | HTTP Verb | Endpoint |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | --------- | -------- |
| `SetWithdrawAddress`          | [MsgSetWithdrawAddress](distribution.md#cosmos.distribution.v1beta1.MsgSetWithdrawAddress)                   | [MsgSetWithdrawAddressResponse](distribution.md#cosmos.distribution.v1beta1.MsgSetWithdrawAddressResponse)                   | SetWithdrawAddress defines a method to change the withdraw address for a delegator (or validator self-delegation). |           |          |
| `WithdrawDelegatorReward`     | [MsgWithdrawDelegatorReward](distribution.md#cosmos.distribution.v1beta1.MsgWithdrawDelegatorReward)         | [MsgWithdrawDelegatorRewardResponse](distribution.md#cosmos.distribution.v1beta1.MsgWithdrawDelegatorRewardResponse)         | WithdrawDelegatorReward defines a method to withdraw rewards of delegator from a single validator.                 |           |          |
| `WithdrawValidatorCommission` | [MsgWithdrawValidatorCommission](distribution.md#cosmos.distribution.v1beta1.MsgWithdrawValidatorCommission) | [MsgWithdrawValidatorCommissionResponse](distribution.md#cosmos.distribution.v1beta1.MsgWithdrawValidatorCommissionResponse) | WithdrawValidatorCommission defines a method to withdraw the full commission to the validator address.             |           |          |
| `FundCommunityPool`           | [MsgFundCommunityPool](distribution.md#cosmos.distribution.v1beta1.MsgFundCommunityPool)                     | [MsgFundCommunityPoolResponse](distribution.md#cosmos.distribution.v1beta1.MsgFundCommunityPoolResponse)                     | FundCommunityPool defines a method to allow an account to directly fund the community pool.                        |           |          |

