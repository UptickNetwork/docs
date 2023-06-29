## cosmos/crisis/v1beta1/genesis.proto

### GenesisState

GenesisState defines the crisis module's genesis state.

| Field          | Type                                                               | Label | Description                                                                 |
| -------------- | ------------------------------------------------------------------ | ----- | --------------------------------------------------------------------------- |
| `constant_fee` | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) |       | constant_fee is the fee used to verify the invariant in the crisis module. |



## cosmos/crisis/v1beta1/tx.proto

### MsgVerifyInvariant

MsgVerifyInvariant represents a message to verify a particular invariance.

| Field                   | Type                           | Label | Description |
| ----------------------- | ------------------------------ | ----- | ----------- |
| `sender`                | [string](value.md#string) |       |             |
| `invariant_module_name` | [string](value.md#string) |       |             |
| `invariant_route`       | [string](value.md#string) |       |             |

### MsgVerifyInvariantResponse

MsgVerifyInvariantResponse defines the Msg/VerifyInvariant response type.

### Msg

Msg defines the bank Msg service.

| Method Name       | Request Type                                                                 | Response Type                                                                                | Description                                                         | HTTP Verb | Endpoint |
| ----------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- | --------- | -------- |
| `VerifyInvariant` | [MsgVerifyInvariant](crisis.md#cosmos.crisis.v1beta1.MsgVerifyInvariant) | [MsgVerifyInvariantResponse](crisis.md#cosmos.crisis.v1beta1.MsgVerifyInvariantResponse) | VerifyInvariant defines a method to verify a particular invariance. |           |          |

