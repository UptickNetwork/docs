## cosmos/vesting/v1beta1/tx.proto

### MsgCreateVestingAccount

MsgCreateVestingAccount defines a message that enables creating a vesting account.

| Field          | Type                                                               | Label    | Description |
| -------------- | ------------------------------------------------------------------ | -------- | ----------- |
| `from_address` | [string](value.md#string)                                     |          |             |
| `to_address`   | [string](value.md#string)                                     |          |             |
| `amount`       | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |
| `end_time`     | [int64](value.md#int64)                                       |          |             |
| `delayed`      | [bool](value.md#bool)                                         |          |             |

### MsgCreateVestingAccountResponse

MsgCreateVestingAccountResponse defines the Msg/CreateVestingAccount response type.

### Msg

Msg defines the bank Msg service.

| Method Name            | Request Type                                                                            | Response Type                                                                                           | Description                                                                    | HTTP Verb | Endpoint |
| ---------------------- | --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | --------- | -------- |
| `CreateVestingAccount` | [MsgCreateVestingAccount](vesting.md#cosmos.vesting.v1beta1.MsgCreateVestingAccount) | [MsgCreateVestingAccountResponse](vesting.md#cosmos.vesting.v1beta1.MsgCreateVestingAccountResponse) | CreateVestingAccount defines a method that enables creating a vesting account. |           |          |



## cosmos/vesting/v1beta1/vesting.proto

### BaseVestingAccount

BaseVestingAccount implements the VestingAccount interface. It contains all the necessary fields needed for any vesting account implementation.

| Field               | Type                                                                             | Label    | Description |
| ------------------- | -------------------------------------------------------------------------------- | -------- | ----------- |
| `base_account`      | [cosmos.auth.v1beta1.BaseAccount](auth.md#cosmos.auth.v1beta1.BaseAccount) |          |             |
| `original_vesting`  | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin)               | repeated |             |
| `delegated_free`    | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin)               | repeated |             |
| `delegated_vesting` | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin)               | repeated |             |
| `end_time`          | [int64](value.md#int64)                                                     |          |             |

### ContinuousVestingAccount

ContinuousVestingAccount implements the VestingAccount interface. It continuously vests by unlocking coins linearly with respect to time.

| Field                  | Type                                                                          | Label | Description |
| ---------------------- | ----------------------------------------------------------------------------- | ----- | ----------- |
| `base_vesting_account` | [BaseVestingAccount](vesting.md#cosmos.vesting.v1beta1.BaseVestingAccount) |       |             |
| `start_time`           | [int64](value.md#int64)                                                  |       |             |

### DelayedVestingAccount

DelayedVestingAccount implements the VestingAccount interface. It vests all coins after a specific time, but non prior. In other words, it keeps them locked until a specified time.

| Field                  | Type                                                                          | Label | Description |
| ---------------------- | ----------------------------------------------------------------------------- | ----- | ----------- |
| `base_vesting_account` | [BaseVestingAccount](vesting.md#cosmos.vesting.v1beta1.BaseVestingAccount) |       |             |

### Period

Period defines a length of time and amount of coins that will vest.

| Field    | Type                                                               | Label    | Description |
| -------- | ------------------------------------------------------------------ | -------- | ----------- |
| `length` | [int64](value.md#int64)                                       |          |             |
| `amount` | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |

### PeriodicVestingAccount

PeriodicVestingAccount implements the VestingAccount interface. It periodically vests by unlocking coins during each specified period.

| Field                  | Type                                                                          | Label    | Description |
| ---------------------- | ----------------------------------------------------------------------------- | -------- | ----------- |
| `base_vesting_account` | [BaseVestingAccount](vesting.md#cosmos.vesting.v1beta1.BaseVestingAccount) |          |             |
| `start_time`           | [int64](value.md#int64)                                                  |          |             |
| `vesting_periods`      | [Period](vesting.md#cosmos.vesting.v1beta1.Period)                         | repeated |             |

