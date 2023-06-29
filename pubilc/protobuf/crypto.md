## cosmos/crypto/ed25519/keys.proto

### PrivKey

PrivKey defines a ed25519 private key.

| Field | Type                         | Label | Description |
| ----- | ---------------------------- | ----- | ----------- |
| `key` | [bytes](value.md#bytes) |       |             |

### PubKey

PubKey defines a ed25519 public key Key is the compressed form of the pubkey. The first byte depends is a 0x02 byte if the y-coordinate is the lexicographically largest of the two associated with the x-coordinate. Otherwise the first byte is a 0x03. This prefix is followed with the x-coordinate.

| Field | Type                         | Label | Description |
| ----- | ---------------------------- | ----- | ----------- |
| `key` | [bytes](value.md#bytes) |       |             |



## cosmos/crypto/multisig/keys.proto

### LegacyAminoPubKey

LegacyAminoPubKey specifies a public key type which nests multiple public keys and a threshold, it uses legacy amino address rules.

| Field         | Type                                                     | Label    | Description |
| ------------- | -------------------------------------------------------- | -------- | ----------- |
| `threshold`   | [uint32](value.md#uint32)                           |          |             |
| `public_keys` | google.protobuf.Any | repeated |             |



## cosmos/crypto/multisig/v1beta1/multisig.proto

### CompactBitArray

CompactBitArray is an implementation of a space efficient bit array. This is used to ensure that the encoded data takes up a minimal amount of space after proto encoding. This is not thread safe, and is not intended for concurrent usage.

| Field               | Type                           | Label | Description |
| ------------------- | ------------------------------ | ----- | ----------- |
| `extra_bits_stored` | [uint32](value.md#uint32) |       |             |
| `elems`             | [bytes](value.md#bytes)   |       |             |

### MultiSignature

MultiSignature wraps the signatures from a multisig.LegacyAminoPubKey. See cosmos.tx.v1betata1.ModeInfo.Multi for how to specify which signers signed and with which modes.

| Field        | Type                         | Label    | Description |
| ------------ | ---------------------------- | -------- | ----------- |
| `signatures` | [bytes](value.md#bytes) | repeated |             |



## cosmos/crypto/secp256k1/keys.proto

### PrivKey

PrivKey defines a secp256k1 private key.

| Field | Type                         | Label | Description |
| ----- | ---------------------------- | ----- | ----------- |
| `key` | [bytes](value.md#bytes) |       |             |

### PubKey

PubKey defines a secp256k1 public key Key is the compressed form of the pubkey. The first byte depends is a 0x02 byte if the y-coordinate is the lexicographically largest of the two associated with the x-coordinate. Otherwise the first byte is a 0x03. This prefix is followed with the x-coordinate.

| Field | Type                         | Label | Description |
| ----- | ---------------------------- | ----- | ----------- |
| `key` | [bytes](value.md#bytes) |       |             |

