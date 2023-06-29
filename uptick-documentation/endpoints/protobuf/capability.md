## cosmos/capability/v1beta1/capability.proto

### Capability

Capability defines an implementation of an object capability. The index provided to a Capability must be globally unique.

| Field   | Type                           | Label | Description |
| ------- | ------------------------------ | ----- | ----------- |
| `index` | [uint64](value.md#uint64) |       |             |

### CapabilityOwners

CapabilityOwners defines a set of owners of a single Capability. The set of owners must be unique.

| Field    | Type                                                   | Label    | Description |
| -------- | ------------------------------------------------------ | -------- | ----------- |
| `owners` | [Owner](capability.md#cosmos.capability.v1beta1.Owner) | repeated |             |

### Owner

Owner defines a single capability owner. An owner is defined by the name of capability and the module name.

| Field    | Type                           | Label | Description |
| -------- | ------------------------------ | ----- | ----------- |
| `module` | [string](value.md#string) |       |             |
| `name`   | [string](value.md#string) |       |             |



## cosmos/capability/v1beta1/genesis.proto

### GenesisOwners

GenesisOwners defines the capability owners with their corresponding index.

| Field          | Type                                                                         | Label | Description                                      |
| -------------- | ---------------------------------------------------------------------------- | ----- | ------------------------------------------------ |
| `index`        | [uint64](value.md#uint64)                                               |       | index is the index of the capability owner.      |
| `index_owners` | [CapabilityOwners](capability.md#cosmos.capability.v1beta1.CapabilityOwners) |       | index_owners are the owners at the given index. |

### GenesisState

GenesisState defines the capability module's genesis state.

| Field    | Type                                                                   | Label    | Description                                                                                                          |
| -------- | ---------------------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------- |
| `index`  | [uint64](value.md#uint64)                                         |          | index is the capability global index.                                                                                |
| `owners` | [GenesisOwners](capability.md#cosmos.capability.v1beta1.GenesisOwners) | repeated | owners represents a map from index to owners of the capability index index key is string to allow amino marshalling. |

