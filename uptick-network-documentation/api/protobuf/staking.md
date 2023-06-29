## cosmos/staking/v1beta1/staking.proto

### Commission

Commission defines commission parameters for a given validator.

| Field              | Type                                                                    | Label | Description                                                                                 |
| ------------------ | ----------------------------------------------------------------------- | ----- | ------------------------------------------------------------------------------------------- |
| `commission_rates` | [CommissionRates](staking.md#cosmos.staking.v1beta1.CommissionRates) |       | commission_rates defines the initial commission rates to be used for creating a validator. |
| `update_time`      | [google.protobuf.Timestamp](#google.protobuf.Timestamp)    |       | update_time is the last time the commission rate was changed.                              |

### CommissionRates

CommissionRates defines the initial commission rates to be used for creating a validator.

| Field             | Type                           | Label | Description                                                                                      |
| ----------------- | ------------------------------ | ----- | ------------------------------------------------------------------------------------------------ |
| `rate`            | [string](value.md#string) |       | rate is the commission rate charged to delegators, as a fraction.                                |
| `max_rate`        | [string](value.md#string) |       | max_rate defines the maximum commission rate which validator can ever charge, as a fraction.    |
| `max_change_rate` | [string](value.md#string) |       | max_change_rate defines the maximum daily increase of the validator commission, as a fraction. |

### DVPair

DVPair is struct that just has a delegator-validator pair with no other data. It is intended to be used as a marshalable pointer. For example, a DVPair can be used to construct the key to getting an UnbondingDelegation from state.

| Field               | Type                           | Label | Description |
| ------------------- | ------------------------------ | ----- | ----------- |
| `delegator_address` | [string](value.md#string) |       |             |
| `validator_address` | [string](value.md#string) |       |             |

### DVPairs

DVPairs defines an array of DVPair objects.

| Field   | Type                                                  | Label    | Description |
| ------- | ----------------------------------------------------- | -------- | ----------- |
| `pairs` | [DVPair](staking.md#cosmos.staking.v1beta1.DVPair) | repeated |             |

### DVVTriplet

DVVTriplet is struct that just has a delegator-validator-validator triplet with no other data. It is intended to be used as a marshalable pointer. For example, a DVVTriplet can be used to construct the key to getting a Redelegation from state.

| Field                   | Type                           | Label | Description |
| ----------------------- | ------------------------------ | ----- | ----------- |
| `delegator_address`     | [string](value.md#string) |       |             |
| `validator_src_address` | [string](value.md#string) |       |             |
| `validator_dst_address` | [string](value.md#string) |       |             |

### DVVTriplets

DVVTriplets defines an array of DVVTriplet objects.

| Field      | Type                                                          | Label    | Description |
| ---------- | ------------------------------------------------------------- | -------- | ----------- |
| `triplets` | [DVVTriplet](staking.md#cosmos.staking.v1beta1.DVVTriplet) | repeated |             |

### Delegation

Delegation represents the bond with tokens held by an account. It is owned by one delegator, and is associated with the voting power of one validator.

| Field               | Type                           | Label | Description                                                        |
| ------------------- | ------------------------------ | ----- | ------------------------------------------------------------------ |
| `delegator_address` | [string](value.md#string) |       | delegator_address is the bech32-encoded address of the delegator. |
| `validator_address` | [string](value.md#string) |       | validator_address is the bech32-encoded address of the validator. |
| `shares`            | [string](value.md#string) |       | shares define the delegation shares received.                      |

### DelegationResponse

DelegationResponse is equivalent to Delegation except that it contains a balance in addition to shares which is more suitable for client responses.

| Field        | Type                                                               | Label | Description |
| ------------ | ------------------------------------------------------------------ | ----- | ----------- |
| `delegation` | [Delegation](staking.md#cosmos.staking.v1beta1.Delegation)      |       |             |
| `balance`    | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) |       |             |

### Description

Description defines a validator description.

| Field              | Type                           | Label | Description                                                             |
| ------------------ | ------------------------------ | ----- | ----------------------------------------------------------------------- |
| `moniker`          | [string](value.md#string) |       | moniker defines a human-readable name for the validator.                |
| `identity`         | [string](value.md#string) |       | identity defines an optional identity signature (ex. UPort or Keybase). |
| `website`          | [string](value.md#string) |       | website defines an optional website link.                               |
| `security_contact` | [string](value.md#string) |       | security_contact defines an optional email for security contact.       |
| `details`          | [string](value.md#string) |       | details define other optional details.                                  |

### HistoricalInfo

HistoricalInfo contains header and validator information for a given block. It is stored as part of staking module's state, which persists the `n` most recent HistoricalInfo (`n` is set by the staking module's `historical_entries` parameter).

| Field    | Type                                                             | Label    | Description |
| -------- | ---------------------------------------------------------------- | -------- | ----------- |
| `header` | tendermint.types.Header |          |             |
| `valset` | [Validator](staking.md#cosmos.staking.v1beta1.Validator)      | repeated |             |

### Params

Params defines the parameters for the staking module.

| Field                | Type                                                               | Label | Description                                                                                      |
| -------------------- | ------------------------------------------------------------------ | ----- | ------------------------------------------------------------------------------------------------ |
| `unbonding_time`     | google.protobuf.Duration |       | unbonding_time is the time duration of unbonding.                                               |
| `max_validators`     | [uint32](value.md#uint32)                                     |       | max_validators is the maximum number of validators.                                             |
| `max_entries`        | [uint32](value.md#uint32)                                     |       | max_entries is the max entries for either unbonding delegation or redelegation (per pair/trio). |
| `historical_entries` | [uint32](value.md#uint32)                                     |       | historical_entries is the number of historical entries to persist.                              |
| `bond_denom`         | [string](value.md#string)                                     |       | bond_denom defines the bondable coin denomination.                                              |

### Pool

Pool is used for tracking bonded and not-bonded token supply of the bond denomination.

| Field               | Type                           | Label | Description |
| ------------------- | ------------------------------ | ----- | ----------- |
| `not_bonded_tokens` | [string](value.md#string) |       |             |
| `bonded_tokens`     | [string](value.md#string) |       |             |

### Redelegation

Redelegation contains the list of a particular delegator's redelegating bonds from a particular source validator to a particular destination validator.

| Field                   | Type                                                                        | Label    | Description                                                                         |
| ----------------------- | --------------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------- |
| `delegator_address`     | [string](value.md#string)                                              |          | delegator_address is the bech32-encoded address of the delegator.                  |
| `validator_src_address` | [string](value.md#string)                                              |          | validator_src_address is the validator redelegation source operator address.      |
| `validator_dst_address` | [string](value.md#string)                                              |          | validator_dst_address is the validator redelegation destination operator address. |
| `entries`               | [RedelegationEntry](staking.md#cosmos.staking.v1beta1.RedelegationEntry) | repeated | entries are the redelegation entries.                                               |

redelegation entries |

### RedelegationEntry

RedelegationEntry defines a redelegation object with relevant metadata.

| Field             | Type                                                                 | Label | Description                                                                        |
| ----------------- | -------------------------------------------------------------------- | ----- | ---------------------------------------------------------------------------------- |
| `creation_height` | [int64](value.md#int64)                                         |       | creation_height defines the height which the redelegation took place.             |
| `completion_time` | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |       | completion_time defines the unix time for redelegation completion.                |
| `initial_balance` | [string](value.md#string)                                       |       | initial_balance defines the initial balance when redelegation started.            |
| `shares_dst`      | [string](value.md#string)                                       |       | shares_dst is the amount of destination-validator shares created by redelegation. |

### RedelegationEntryResponse

RedelegationEntryResponse is equivalent to a RedelegationEntry except that it contains a balance in addition to shares which is more suitable for client responses.

| Field                | Type                                                                        | Label | Description |
| -------------------- | --------------------------------------------------------------------------- | ----- | ----------- |
| `redelegation_entry` | [RedelegationEntry](staking.md#cosmos.staking.v1beta1.RedelegationEntry) |       |             |
| `balance`            | [string](value.md#string)                                              |       |             |

### RedelegationResponse

RedelegationResponse is equivalent to a Redelegation except that its entries contain a balance in addition to shares which is more suitable for client responses.

| Field          | Type                                                                                        | Label    | Description |
| -------------- | ------------------------------------------------------------------------------------------- | -------- | ----------- |
| `redelegation` | [Redelegation](staking.md#cosmos.staking.v1beta1.Redelegation)                           |          |             |
| `entries`      | [RedelegationEntryResponse](staking.md#cosmos.staking.v1beta1.RedelegationEntryResponse) | repeated |             |

### UnbondingDelegation

UnbondingDelegation stores all of a single delegator's unbonding bonds for a single validator in an time-ordered list.

| Field               | Type                                                                                      | Label    | Description                                                        |
| ------------------- | ----------------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------ |
| `delegator_address` | [string](value.md#string)                                                            |          | delegator_address is the bech32-encoded address of the delegator. |
| `validator_address` | [string](value.md#string)                                                            |          | validator_address is the bech32-encoded address of the validator. |
| `entries`           | [UnbondingDelegationEntry](staking.md#cosmos.staking.v1beta1.UnbondingDelegationEntry) | repeated | entries are the unbonding delegation entries.                      |

unbonding delegation entries |

### UnbondingDelegationEntry

UnbondingDelegationEntry defines an unbonding object with relevant metadata.

| Field             | Type                                                                 | Label | Description                                                                       |
| ----------------- | -------------------------------------------------------------------- | ----- | --------------------------------------------------------------------------------- |
| `creation_height` | [int64](value.md#int64)                                         |       | creation_height is the height which the unbonding took place.                    |
| `completion_time` | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |       | completion_time is the unix time for unbonding completion.                       |
| `initial_balance` | [string](value.md#string)                                       |       | initial_balance defines the tokens initially scheduled to receive at completion. |
| `balance`         | [string](value.md#string)                                       |       | balance defines the tokens to receive at completion.                              |

### ValAddresses

ValAddresses defines a repeated set of validator addresses.

| Field       | Type                           | Label    | Description |
| ----------- | ------------------------------ | -------- | ----------- |
| `addresses` | [string](value.md#string) | repeated |             |

### Validator

Validator defines a validator, together with the total amount of the Validator's bond shares and their exchange rate to coins. Slashing results in a decrease in the exchange rate, allowing correct calculation of future undelegations without iterating over delegators. When coins are delegated to this validator, the validator is credited with a delegation whose number of bond shares is based on the amount of coins delegated divided by the current exchange rate. Voting power can be calculated as total bonded shares multiplied by exchange rate.

| Field                 | Type                                                                 | Label | Description                                                                                      |
| --------------------- | -------------------------------------------------------------------- | ----- | ------------------------------------------------------------------------------------------------ |
| `operator_address`    | [string](value.md#string)                                       |       | operator_address defines the address of the validator's operator; bech encoded in JSON.         |
| `consensus_pubkey`    | google.protobuf.Any             |       | consensus_pubkey is the consensus public key of the validator, as a Protobuf Any.               |
| `jailed`              | [bool](value.md#bool)                                           |       | jailed defined whether the validator has been jailed from bonded status or not.                  |
| `status`              | [BondStatus](staking.md#cosmos.staking.v1beta1.BondStatus)        |       | status is the validator status (bonded/unbonding/unbonded).                                      |
| `tokens`              | [string](value.md#string)                                       |       | tokens define the delegated tokens (incl. self-delegation).                                      |
| `delegator_shares`    | [string](value.md#string)                                       |       | delegator_shares defines total shares issued to a validator's delegators.                       |
| `description`         | [Description](staking.md#cosmos.staking.v1beta1.Description)      |       | description defines the description terms for the validator.                                     |
| `unbonding_height`    | [int64](value.md#int64)                                         |       | unbonding_height defines, if unbonding, the height at which this validator has begun unbonding. |
| `unbonding_time`      | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |       | unbonding_time defines, if unbonding, the min time for the validator to complete unbonding.     |
| `commission`          | [Commission](staking.md#cosmos.staking.v1beta1.Commission)        |       | commission defines the commission parameters.                                                    |
| `min_self_delegation` | [string](value.md#string)                                       |       | min_self_delegation is the validator's self declared minimum self delegation.                  |

### BondStatus

BondStatus is the status of a validator.

| Name                      | Number | Description                                      |
| ------------------------- | ------ | ------------------------------------------------ |
| BOND_STATUS_UNSPECIFIED | 0      | UNSPECIFIED defines an invalid validator status. |
| BOND_STATUS_UNBONDED    | 1      | UNBONDED defines a validator that is not bonded. |
| BOND_STATUS_UNBONDING   | 2      | UNBONDING defines a validator that is unbonding. |
| BOND_STATUS_BONDED      | 3      | BONDED defines a validator that is bonded.       |



## cosmos/staking/v1beta1/genesis.proto

### GenesisState

GenesisState defines the staking module's genesis state.

| Field                   | Type                                                                            | Label    | Description                                                                                                       |
| ----------------------- | ------------------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| `params`                | [Params](staking.md#cosmos.staking.v1beta1.Params)                           |          | params defines all the paramaters of related to deposit.                                                          |
| `last_total_power`      | [bytes](value.md#bytes)                                                    |          | last_total_power tracks the total amounts of bonded tokens recorded during the previous end block.              |
| `last_validator_powers` | [LastValidatorPower](staking.md#cosmos.staking.v1beta1.LastValidatorPower)   | repeated | last_validator_powers is a special index that provides a historical list of the last-block's bonded validators. |
| `validators`            | [Validator](staking.md#cosmos.staking.v1beta1.Validator)                     | repeated | delegations defines the validator set at genesis.                                                                 |
| `delegations`           | [Delegation](staking.md#cosmos.staking.v1beta1.Delegation)                   | repeated | delegations defines the delegations active at genesis.                                                            |
| `unbonding_delegations` | [UnbondingDelegation](staking.md#cosmos.staking.v1beta1.UnbondingDelegation) | repeated | unbonding_delegations defines the unbonding delegations active at genesis.                                       |
| `redelegations`         | [Redelegation](staking.md#cosmos.staking.v1beta1.Redelegation)               | repeated | redelegations defines the redelegations active at genesis.                                                        |
| `exported`              | [bool](value.md#bool)                                                      |          |                                                                                                                   |

### LastValidatorPower

LastValidatorPower required for validator set update logic.

| Field     | Type                           | Label | Description                               |
| --------- | ------------------------------ | ----- | ----------------------------------------- |
| `address` | [string](value.md#string) |       | address is the address of the validator.  |
| `power`   | [int64](value.md#int64)   |       | power defines the power of the validator. |



## cosmos/staking/v1beta1/query.proto

### QueryDelegationRequest

QueryDelegationRequest is request type for the Query/Delegation RPC method.

| Field            | Type                           | Label | Description                                                 |
| ---------------- | ------------------------------ | ----- | ----------------------------------------------------------- |
| `delegator_addr` | [string](value.md#string) |       | delegator_addr defines the delegator address to query for. |
| `validator_addr` | [string](value.md#string) |       | validator_addr defines the validator address to query for. |

### QueryDelegationResponse

QueryDelegationResponse is response type for the Query/Delegation RPC method.

| Field                 | Type                                                                          | Label | Description                                                        |
| --------------------- | ----------------------------------------------------------------------------- | ----- | ------------------------------------------------------------------ |
| `delegation_response` | [DelegationResponse](staking.md#cosmos.staking.v1beta1.DelegationResponse) |       | delegation_responses defines the delegation info of a delegation. |

### QueryDelegatorDelegationsRequest

QueryDelegatorDelegationsRequest is request type for the Query/DelegatorDelegations RPC method.

| Field            | Type                                                                                         | Label | Description                                                 |
| ---------------- | -------------------------------------------------------------------------------------------- | ----- | ----------------------------------------------------------- |
| `delegator_addr` | [string](value.md#string)                                                               |       | delegator_addr defines the delegator address to query for. |
| `pagination`     | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request.  |

### QueryDelegatorDelegationsResponse

QueryDelegatorDelegationsResponse is response type for the Query/DelegatorDelegations RPC method.

| Field                  | Type                                                                                           | Label    | Description                                                             |
| ---------------------- | ---------------------------------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------- |
| `delegation_responses` | [DelegationResponse](staking.md#cosmos.staking.v1beta1.DelegationResponse)                  | repeated | delegation_responses defines all the delegations' info of a delegator. |
| `pagination`           | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response.                      |

### QueryDelegatorUnbondingDelegationsRequest

QueryDelegatorUnbondingDelegationsRequest is request type for the Query/DelegatorUnbondingDelegations RPC method.

| Field            | Type                                                                                         | Label | Description                                                 |
| ---------------- | -------------------------------------------------------------------------------------------- | ----- | ----------------------------------------------------------- |
| `delegator_addr` | [string](value.md#string)                                                               |       | delegator_addr defines the delegator address to query for. |
| `pagination`     | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request.  |

### QueryDelegatorUnbondingDelegationsResponse

QueryUnbondingDelegatorDelegationsResponse is response type for the Query/UnbondingDelegatorDelegations RPC method.

| Field                 | Type                                                                                           | Label    | Description                                        |
| --------------------- | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `unbonding_responses` | [UnbondingDelegation](staking.md#cosmos.staking.v1beta1.UnbondingDelegation)                | repeated |                                                    |
| `pagination`          | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### QueryDelegatorValidatorRequest

QueryDelegatorValidatorRequest is request type for the Query/DelegatorValidator RPC method.

| Field            | Type                           | Label | Description                                                 |
| ---------------- | ------------------------------ | ----- | ----------------------------------------------------------- |
| `delegator_addr` | [string](value.md#string) |       | delegator_addr defines the delegator address to query for. |
| `validator_addr` | [string](value.md#string) |       | validator_addr defines the validator address to query for. |

### QueryDelegatorValidatorResponse

QueryDelegatorValidatorResponse response type for the Query/DelegatorValidator RPC method.

| Field       | Type                                                        | Label | Description                               |
| ----------- | ----------------------------------------------------------- | ----- | ----------------------------------------- |
| `validator` | [Validator](staking.md#cosmos.staking.v1beta1.Validator) |       | validator defines the the validator info. |

### QueryDelegatorValidatorsRequest

QueryDelegatorValidatorsRequest is request type for the Query/DelegatorValidators RPC method.

| Field            | Type                                                                                         | Label | Description                                                 |
| ---------------- | -------------------------------------------------------------------------------------------- | ----- | ----------------------------------------------------------- |
| `delegator_addr` | [string](value.md#string)                                                               |       | delegator_addr defines the delegator address to query for. |
| `pagination`     | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request.  |

### QueryDelegatorValidatorsResponse

QueryDelegatorValidatorsResponse is response type for the Query/DelegatorValidators RPC method.

| Field        | Type                                                                                           | Label    | Description                                                 |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | ----------------------------------------------------------- |
| `validators` | [Validator](staking.md#cosmos.staking.v1beta1.Validator)                                    | repeated | validators defines the the validators' info of a delegator. |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response.          |

### QueryHistoricalInfoRequest

QueryHistoricalInfoRequest is request type for the Query/HistoricalInfo RPC method.

| Field    | Type                         | Label | Description                                                  |
| -------- | ---------------------------- | ----- | ------------------------------------------------------------ |
| `height` | [int64](value.md#int64) |       | height defines at which height to query the historical info. |

### QueryHistoricalInfoResponse

QueryHistoricalInfoResponse is response type for the Query/HistoricalInfo RPC method.

| Field  | Type                                                                  | Label | Description                                           |
| ------ | --------------------------------------------------------------------- | ----- | ----------------------------------------------------- |
| `hist` | [HistoricalInfo](staking.md#cosmos.staking.v1beta1.HistoricalInfo) |       | hist defines the historical info at the given height. |

### QueryParamsRequest

QueryParamsRequest is request type for the Query/Params RPC method.

### QueryParamsResponse

QueryParamsResponse is response type for the Query/Params RPC method.

| Field    | Type                                                  | Label | Description                                     |
| -------- | ----------------------------------------------------- | ----- | ----------------------------------------------- |
| `params` | [Params](staking.md#cosmos.staking.v1beta1.Params) |       | params holds all the parameters of this module. |

### QueryPoolRequest

QueryPoolRequest is request type for the Query/Pool RPC method.

### QueryPoolResponse

QueryPoolResponse is response type for the Query/Pool RPC method.

| Field  | Type                                              | Label | Description                 |
| ------ | ------------------------------------------------- | ----- | --------------------------- |
| `pool` | [Pool](staking.md#cosmos.staking.v1beta1.Pool) |       | pool defines the pool info. |

### QueryRedelegationsRequest

QueryRedelegationsRequest is request type for the Query/Redelegations RPC method.

| Field                | Type                                                                                         | Label | Description                                                            |
| -------------------- | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------------------- |
| `delegator_addr`     | [string](value.md#string)                                                               |       | delegator_addr defines the delegator address to query for.            |
| `src_validator_addr` | [string](value.md#string)                                                               |       | src_validator_addr defines the validator address to redelegate from. |
| `dst_validator_addr` | [string](value.md#string)                                                               |       | dst_validator_addr defines the validator address to redelegate to.   |
| `pagination`         | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request.             |

### QueryRedelegationsResponse

QueryRedelegationsResponse is response type for the Query/Redelegations RPC method.

| Field                    | Type                                                                                           | Label    | Description                                        |
| ------------------------ | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `redelegation_responses` | [RedelegationResponse](staking.md#cosmos.staking.v1beta1.RedelegationResponse)              | repeated |                                                    |
| `pagination`             | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### QueryUnbondingDelegationRequest

QueryUnbondingDelegationRequest is request type for the Query/UnbondingDelegation RPC method.

| Field            | Type                           | Label | Description                                                 |
| ---------------- | ------------------------------ | ----- | ----------------------------------------------------------- |
| `delegator_addr` | [string](value.md#string) |       | delegator_addr defines the delegator address to query for. |
| `validator_addr` | [string](value.md#string) |       | validator_addr defines the validator address to query for. |

### QueryUnbondingDelegationResponse

QueryDelegationResponse is response type for the Query/UnbondingDelegation RPC method.

| Field    | Type                                                                            | Label | Description                                               |
| -------- | ------------------------------------------------------------------------------- | ----- | --------------------------------------------------------- |
| `unbond` | [UnbondingDelegation](staking.md#cosmos.staking.v1beta1.UnbondingDelegation) |       | unbond defines the unbonding information of a delegation. |

### QueryValidatorDelegationsRequest

QueryValidatorDelegationsRequest is request type for the Query/ValidatorDelegations RPC method

| Field            | Type                                                                                         | Label | Description                                                 |
| ---------------- | -------------------------------------------------------------------------------------------- | ----- | ----------------------------------------------------------- |
| `validator_addr` | [string](value.md#string)                                                               |       | validator_addr defines the validator address to query for. |
| `pagination`     | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request.  |

### QueryValidatorDelegationsResponse

QueryValidatorDelegationsResponse is response type for the Query/ValidatorDelegations RPC method

| Field                  | Type                                                                                           | Label    | Description                                        |
| ---------------------- | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `delegation_responses` | [DelegationResponse](staking.md#cosmos.staking.v1beta1.DelegationResponse)                  | repeated |                                                    |
| `pagination`           | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### QueryValidatorRequest

QueryValidatorRequest is response type for the Query/Validator RPC method

| Field            | Type                           | Label | Description                                                 |
| ---------------- | ------------------------------ | ----- | ----------------------------------------------------------- |
| `validator_addr` | [string](value.md#string) |       | validator_addr defines the validator address to query for. |

### QueryValidatorResponse

QueryValidatorResponse is response type for the Query/Validator RPC method

| Field       | Type                                                        | Label | Description                               |
| ----------- | ----------------------------------------------------------- | ----- | ----------------------------------------- |
| `validator` | [Validator](staking.md#cosmos.staking.v1beta1.Validator) |       | validator defines the the validator info. |

### QueryValidatorUnbondingDelegationsRequest

QueryValidatorUnbondingDelegationsRequest is required type for the Query/ValidatorUnbondingDelegations RPC method

| Field            | Type                                                                                         | Label | Description                                                 |
| ---------------- | -------------------------------------------------------------------------------------------- | ----- | ----------------------------------------------------------- |
| `validator_addr` | [string](value.md#string)                                                               |       | validator_addr defines the validator address to query for. |
| `pagination`     | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request.  |

### QueryValidatorUnbondingDelegationsResponse

QueryValidatorUnbondingDelegationsResponse is response type for the Query/ValidatorUnbondingDelegations RPC method.

| Field                 | Type                                                                                           | Label    | Description                                        |
| --------------------- | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `unbonding_responses` | [UnbondingDelegation](staking.md#cosmos.staking.v1beta1.UnbondingDelegation)                | repeated |                                                    |
| `pagination`          | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### QueryValidatorsRequest

QueryValidatorsRequest is request type for Query/Validators RPC method.

| Field        | Type                                                                                         | Label | Description                                                     |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | --------------------------------------------------------------- |
| `status`     | [string](value.md#string)                                                               |       | status enables to query for validators matching a given status. |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request.      |

### QueryValidatorsResponse

QueryValidatorsResponse is response type for the Query/Validators RPC method

| Field        | Type                                                                                           | Label    | Description                                        |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `validators` | [Validator](staking.md#cosmos.staking.v1beta1.Validator)                                    | repeated | validators contains all the queried validators.    |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### Query

Query defines the gRPC querier service.

| Method Name                     | Request Type                                                                                                                | Response Type                                                                                                                 | Description                                                                                   | HTTP Verb | Endpoint                                                                                                 |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------- | -------------------------------------------------------------------------------------------------------- |
| `Validators`                    | [QueryValidatorsRequest](staking.md#cosmos.staking.v1beta1.QueryValidatorsRequest)                                       | [QueryValidatorsResponse](staking.md#cosmos.staking.v1beta1.QueryValidatorsResponse)                                       | Validators queries all validators that match the given status.                                | GET       | /cosmos/staking/v1beta1/validators                                                                       |
| `Validator`                     | [QueryValidatorRequest](staking.md#cosmos.staking.v1beta1.QueryValidatorRequest)                                         | [QueryValidatorResponse](staking.md#cosmos.staking.v1beta1.QueryValidatorResponse)                                         | Validator queries validator info for given validator address.                                 | GET       | /cosmos/staking/v1beta1/validators/{validator_addr}                                                     |
| `ValidatorDelegations`          | [QueryValidatorDelegationsRequest](staking.md#cosmos.staking.v1beta1.QueryValidatorDelegationsRequest)                   | [QueryValidatorDelegationsResponse](staking.md#cosmos.staking.v1beta1.QueryValidatorDelegationsResponse)                   | ValidatorDelegations queries delegate info for given validator.                               | GET       | /cosmos/staking/v1beta1/validators/{validator_addr}/delegations                                         |
| `ValidatorUnbondingDelegations` | [QueryValidatorUnbondingDelegationsRequest](staking.md#cosmos.staking.v1beta1.QueryValidatorUnbondingDelegationsRequest) | [QueryValidatorUnbondingDelegationsResponse](staking.md#cosmos.staking.v1beta1.QueryValidatorUnbondingDelegationsResponse) | ValidatorUnbondingDelegations queries unbonding delegations of a validator.                   | GET       | /cosmos/staking/v1beta1/validators/{validator_addr}/unbonding_delegations                              |
| `Delegation`                    | [QueryDelegationRequest](staking.md#cosmos.staking.v1beta1.QueryDelegationRequest)                                       | [QueryDelegationResponse](staking.md#cosmos.staking.v1beta1.QueryDelegationResponse)                                       | Delegation queries delegate info for given validator delegator pair.                          | GET       | /cosmos/staking/v1beta1/validators/{validator_addr}/delegations/{delegator_addr}                       |
| `UnbondingDelegation`           | [QueryUnbondingDelegationRequest](staking.md#cosmos.staking.v1beta1.QueryUnbondingDelegationRequest)                     | [QueryUnbondingDelegationResponse](staking.md#cosmos.staking.v1beta1.QueryUnbondingDelegationResponse)                     | UnbondingDelegation queries unbonding info for given validator delegator pair.                | GET       | /cosmos/staking/v1beta1/validators/{validator_addr}/delegations/{delegator_addr}/unbonding_delegation |
| `DelegatorDelegations`          | [QueryDelegatorDelegationsRequest](staking.md#cosmos.staking.v1beta1.QueryDelegatorDelegationsRequest)                   | [QueryDelegatorDelegationsResponse](staking.md#cosmos.staking.v1beta1.QueryDelegatorDelegationsResponse)                   | DelegatorDelegations queries all delegations of a given delegator address.                    | GET       | /cosmos/staking/v1beta1/delegations/{delegator_addr}                                                    |
| `DelegatorUnbondingDelegations` | [QueryDelegatorUnbondingDelegationsRequest](staking.md#cosmos.staking.v1beta1.QueryDelegatorUnbondingDelegationsRequest) | [QueryDelegatorUnbondingDelegationsResponse](staking.md#cosmos.staking.v1beta1.QueryDelegatorUnbondingDelegationsResponse) | DelegatorUnbondingDelegations queries all unbonding delegations of a given delegator address. | GET       | /cosmos/staking/v1beta1/delegators/{delegator_addr}/unbonding_delegations                              |
| `Redelegations`                 | [QueryRedelegationsRequest](staking.md#cosmos.staking.v1beta1.QueryRedelegationsRequest)                                 | [QueryRedelegationsResponse](staking.md#cosmos.staking.v1beta1.QueryRedelegationsResponse)                                 | Redelegations queries redelegations of given address.                                         | GET       | /cosmos/staking/v1beta1/delegators/{delegator_addr}/redelegations                                       |
| `DelegatorValidators`           | [QueryDelegatorValidatorsRequest](staking.md#cosmos.staking.v1beta1.QueryDelegatorValidatorsRequest)                     | [QueryDelegatorValidatorsResponse](staking.md#cosmos.staking.v1beta1.QueryDelegatorValidatorsResponse)                     | DelegatorValidators queries all validators info for given delegator address.                  | GET       | /cosmos/staking/v1beta1/delegators/{delegator_addr}/validators                                          |
| `DelegatorValidator`            | [QueryDelegatorValidatorRequest](staking.md#cosmos.staking.v1beta1.QueryDelegatorValidatorRequest)                       | [QueryDelegatorValidatorResponse](staking.md#cosmos.staking.v1beta1.QueryDelegatorValidatorResponse)                       | DelegatorValidator queries validator info for given delegator validator pair.                 | GET       | /cosmos/staking/v1beta1/delegators/{delegator_addr}/validators/{validator_addr}                        |
| `HistoricalInfo`                | [QueryHistoricalInfoRequest](staking.md#cosmos.staking.v1beta1.QueryHistoricalInfoRequest)                               | [QueryHistoricalInfoResponse](staking.md#cosmos.staking.v1beta1.QueryHistoricalInfoResponse)                               | HistoricalInfo queries the historical info for given height.                                  | GET       | /cosmos/staking/v1beta1/historical_info/{height}                                                        |
| `Pool`                          | [QueryPoolRequest](staking.md#cosmos.staking.v1beta1.QueryPoolRequest)                                                   | [QueryPoolResponse](staking.md#cosmos.staking.v1beta1.QueryPoolResponse)                                                   | Pool queries the pool info.                                                                   | GET       | /cosmos/staking/v1beta1/pool                                                                             |
| `Params`                        | [QueryParamsRequest](staking.md#cosmos.staking.v1beta1.QueryParamsRequest)                                               | [QueryParamsResponse](staking.md#cosmos.staking.v1beta1.QueryParamsResponse)                                               | Parameters queries the staking parameters.                                                    | GET       | /cosmos/staking/v1beta1/params                                                                           |



## cosmos/staking/v1beta1/tx.proto

### MsgBeginRedelegate

MsgBeginRedelegate defines a SDK message for performing a redelegation of coins from a delegator and source validator to a destination validator.

| Field                   | Type                                                               | Label | Description |
| ----------------------- | ------------------------------------------------------------------ | ----- | ----------- |
| `delegator_address`     | [string](value.md#string)                                     |       |             |
| `validator_src_address` | [string](value.md#string)                                     |       |             |
| `validator_dst_address` | [string](value.md#string)                                     |       |             |
| `amount`                | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) |       |             |

### MsgBeginRedelegateResponse

MsgBeginRedelegateResponse defines the Msg/BeginRedelegate response type.

| Field             | Type                                                                 | Label | Description |
| ----------------- | -------------------------------------------------------------------- | ----- | ----------- |
| `completion_time` | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |       |             |

### MsgCreateValidator

MsgCreateValidator defines a SDK message for creating a new validator.

| Field                 | Type                                                                    | Label | Description |
| --------------------- | ----------------------------------------------------------------------- | ----- | ----------- |
| `description`         | [Description](staking.md#cosmos.staking.v1beta1.Description)         |       |             |
| `commission`          | [CommissionRates](staking.md#cosmos.staking.v1beta1.CommissionRates) |       |             |
| `min_self_delegation` | [string](value.md#string)                                          |       |             |
| `delegator_address`   | [string](value.md#string)                                          |       |             |
| `validator_address`   | [string](value.md#string)                                          |       |             |
| `pubkey`              | google.protobuf.Any                |       |             |
| `value`               | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin)      |       |             |

### MsgCreateValidatorResponse

MsgCreateValidatorResponse defines the Msg/CreateValidator response type.

### MsgDelegate

MsgDelegate defines a SDK message for performing a delegation of coins from a delegator to a validator.

| Field               | Type                                                               | Label | Description |
| ------------------- | ------------------------------------------------------------------ | ----- | ----------- |
| `delegator_address` | [string](value.md#string)                                     |       |             |
| `validator_address` | [string](value.md#string)                                     |       |             |
| `amount`            | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) |       |             |

### MsgDelegateResponse

MsgDelegateResponse defines the Msg/Delegate response type.

### MsgEditValidator

MsgEditValidator defines a SDK message for editing an existing validator.

| Field                 | Type                                                            | Label | Description                                                                                                                                                                                                                 |
| --------------------- | --------------------------------------------------------------- | ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `description`         | [Description](staking.md#cosmos.staking.v1beta1.Description) |       |                                                                                                                                                                                                                             |
| `validator_address`   | [string](value.md#string)                                  |       |                                                                                                                                                                                                                             |
| `commission_rate`     | [string](value.md#string)                                  |       | We pass a reference to the new commission rate and min self delegation as it's not mandatory to update. If not updated, the deserialized rate will be zero with no way to distinguish if an update was intended. REF: #2373 |
| `min_self_delegation` | [string](value.md#string)                                  |       |                                                                                                                                                                                                                             |

### MsgEditValidatorResponse

MsgEditValidatorResponse defines the Msg/EditValidator response type.

### MsgUndelegate

MsgUndelegate defines a SDK message for performing an undelegation from a delegate and a validator.

| Field               | Type                                                               | Label | Description |
| ------------------- | ------------------------------------------------------------------ | ----- | ----------- |
| `delegator_address` | [string](value.md#string)                                     |       |             |
| `validator_address` | [string](value.md#string)                                     |       |             |
| `amount`            | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) |       |             |

### MsgUndelegateResponse

MsgUndelegateResponse defines the Msg/Undelegate response type.

| Field             | Type                                                                 | Label | Description |
| ----------------- | -------------------------------------------------------------------- | ----- | ----------- |
| `completion_time` | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |       |             |

### Msg

Msg defines the staking Msg service.

| Method Name       | Request Type                                                                  | Response Type                                                                                 | Description                                                                                                                               | HTTP Verb | Endpoint |
| ----------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | --------- | -------- |
| `CreateValidator` | [MsgCreateValidator](staking.md#cosmos.staking.v1beta1.MsgCreateValidator) | [MsgCreateValidatorResponse](staking.md#cosmos.staking.v1beta1.MsgCreateValidatorResponse) | CreateValidator defines a method for creating a new validator.                                                                            |           |          |
| `EditValidator`   | [MsgEditValidator](staking.md#cosmos.staking.v1beta1.MsgEditValidator)     | [MsgEditValidatorResponse](staking.md#cosmos.staking.v1beta1.MsgEditValidatorResponse)     | EditValidator defines a method for editing an existing validator.                                                                         |           |          |
| `Delegate`        | [MsgDelegate](staking.md#cosmos.staking.v1beta1.MsgDelegate)               | [MsgDelegateResponse](staking.md#cosmos.staking.v1beta1.MsgDelegateResponse)               | Delegate defines a method for performing a delegation of coins from a delegator to a validator.                                           |           |          |
| `BeginRedelegate` | [MsgBeginRedelegate](staking.md#cosmos.staking.v1beta1.MsgBeginRedelegate) | [MsgBeginRedelegateResponse](staking.md#cosmos.staking.v1beta1.MsgBeginRedelegateResponse) | BeginRedelegate defines a method for performing a redelegation of coins from a delegator and source validator to a destination validator. |           |          |
| `Undelegate`      | [MsgUndelegate](staking.md#cosmos.staking.v1beta1.MsgUndelegate)           | [MsgUndelegateResponse](staking.md#cosmos.staking.v1beta1.MsgUndelegateResponse)           | Undelegate defines a method for performing an undelegation from a delegate and a validator.                                               |           |          |

