## uptick/collection/v1/collection.proto

### BaseNFT

BaseNFT defines a non-fungible token

| Field      | Type                           | Label | Description |
| ---------- | ------------------------------ | ----- | ----------- |
| `id`       | [string](value.md#string) |       |             |
| `name`     | [string](value.md#string) |       |             |
| `uri`      | [string](value.md#string) |       |             |
| `data`     | [string](value.md#string) |       |             |
| `owner`    | [string](value.md#string) |       |             |
| `uri_hash` | [string](value.md#string) |       |             |

### Collection

Collection defines a type of collection

| Field   | Type                                                  | Label    | Description |
| ------- | ----------------------------------------------------- | -------- | ----------- |
| `denom` | [Denom](collection.md#uptick.collection.v1.Denom)     |          |             |
| `nfts`  | [BaseNFT](collection.md#uptick.collection.v1.BaseNFT) | repeated |             |

### Denom

Denom defines a type of NFT

| Field               | Type                           | Label | Description |
| ------------------- | ------------------------------ | ----- | ----------- |
| `id`                | [string](value.md#string) |       |             |
| `name`              | [string](value.md#string) |       |             |
| `schema`            | [string](value.md#string) |       |             |
| `creator`           | [string](value.md#string) |       |             |
| `symbol`            | [string](value.md#string) |       |             |
| `mint_restricted`   | [bool](value.md#bool)     |       |             |
| `update_restricted` | [bool](value.md#bool)     |       |             |
| `description`       | [string](value.md#string) |       |             |
| `uri`               | [string](value.md#string) |       |             |
| `uri_hash`          | [string](value.md#string) |       |             |
| `data`              | [string](value.md#string) |       |             |

### DenomMetadata

| Field               | Type                           | Label | Description |
| ------------------- | ------------------------------ | ----- | ----------- |
| `creator`           | [string](value.md#string) |       |             |
| `schema`            | [string](value.md#string) |       |             |
| `mint_restricted`   | [bool](value.md#bool)     |       |             |
| `update_restricted` | [bool](value.md#bool)     |       |             |
| `data`              | [string](value.md#string) |       |             |

### IDCollection

IDCollection defines a type of collection with specified ID

| Field       | Type                           | Label    | Description |
| ----------- | ------------------------------ | -------- | ----------- |
| `denom_id`  | [string](value.md#string) |          |             |
| `token_ids` | [string](value.md#string) | repeated |             |

### NFTMetadata

| Field  | Type                           | Label | Description |
| ------ | ------------------------------ | ----- | ----------- |
| `name` | [string](value.md#string) |       |             |
| `data` | [string](value.md#string) |       |             |

### Owner

Owner defines a type of owner

| Field            | Type                                                            | Label    | Description |
| ---------------- | --------------------------------------------------------------- | -------- | ----------- |
| `address`        | [string](value.md#string)                                  |          |             |
| `id_collections` | [IDCollection](collection.md#uptick.collection.v1.IDCollection) | repeated |             |



## uptick/collection/v1/genesis.proto

### GenesisState

GenesisState defines the collection module's genesis state

| Field         | Type                                                        | Label    | Description |
| ------------- | ----------------------------------------------------------- | -------- | ----------- |
| `collections` | [Collection](collection.md#uptick.collection.v1.Collection) | repeated |             |



## uptick/collection/v1/query.proto

### QueryCollectionRequest

QueryCollectionRequest is the request type for the Query/Collection RPC method

| Field        | Type                                                                                         | Label | Description                                                |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `denom_id`   | [string](value.md#string)                                                               |       |                                                            |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request. |

### QueryCollectionResponse

QueryCollectionResponse is the response type for the Query/Collection RPC method

| Field        | Type                                                                                           | Label | Description |
| ------------ | ---------------------------------------------------------------------------------------------- | ----- | ----------- |
| `collection` | [Collection](collection.md#uptick.collection.v1.Collection)                                    |       |             |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |       |             |

### QueryDenomRequest

QueryDenomRequest is the request type for the Query/Denom RPC method

| Field      | Type                           | Label | Description |
| ---------- | ------------------------------ | ----- | ----------- |
| `denom_id` | [string](value.md#string) |       |             |

### QueryDenomResponse

QueryDenomResponse is the response type for the Query/Denom RPC method

| Field   | Type                                              | Label | Description |
| ------- | ------------------------------------------------- | ----- | ----------- |
| `denom` | [Denom](collection.md#uptick.collection.v1.Denom) |       |             |

### QueryDenomsRequest

QueryDenomsRequest is the request type for the Query/Denoms RPC method

| Field        | Type                                                                                         | Label | Description                                                |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request. |

### QueryDenomsResponse

QueryDenomsResponse is the response type for the Query/Denoms RPC method

| Field        | Type                                                                                           | Label    | Description |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | ----------- |
| `denoms`     | [Denom](collection.md#uptick.collection.v1.Denom)                                              | repeated |             |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          |             |

### QueryNFTRequest

QueryNFTRequest is the request type for the Query/NFT RPC method

| Field      | Type                           | Label | Description |
| ---------- | ------------------------------ | ----- | ----------- |
| `denom_id` | [string](value.md#string) |       |             |
| `token_id` | [string](value.md#string) |       |             |

### QueryNFTResponse

QueryNFTResponse is the response type for the Query/NFT RPC method

| Field | Type                                                  | Label | Description |
| ----- | ----------------------------------------------------- | ----- | ----------- |
| `nft` | [BaseNFT](collection.md#uptick.collection.v1.BaseNFT) |       |             |

### QueryNFTsOfOwnerRequest

QueryNFTsOfOwnerRequest is the request type for the Query/Owner RPC method

| Field        | Type                                                                                         | Label | Description                                                |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `denom_id`   | [string](value.md#string)                                                               |       |                                                            |
| `owner`      | [string](value.md#string)                                                               |       |                                                            |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request. |

### QueryNFTsOfOwnerResponse

QueryNFTsOfOwnerResponse is the response type for the Query/Owner RPC method

| Field        | Type                                                                                           | Label | Description |
| ------------ | ---------------------------------------------------------------------------------------------- | ----- | ----------- |
| `owner`      | [Owner](collection.md#uptick.collection.v1.Owner)                                              |       |             |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |       |             |

### QuerySupplyRequest

QuerySupplyRequest is the request type for the Query/HTLC RPC method

| Field      | Type                           | Label | Description |
| ---------- | ------------------------------ | ----- | ----------- |
| `denom_id` | [string](value.md#string) |       |             |
| `owner`    | [string](value.md#string) |       |             |

### QuerySupplyResponse

QuerySupplyResponse is the response type for the Query/Supply RPC method

| Field    | Type                           | Label | Description |
| -------- | ------------------------------ | ----- | ----------- |
| `amount` | [uint64](value.md#uint64) |       |             |

### Query

Query defines the gRPC querier service for NFT module

| Method Name   | Request Type                                                                          | Response Type                                                                           | Description                                               | HTTP Verb | Endpoint                                          |
| ------------- | ------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------- | --------- | ------------------------------------------------- |
| `Supply`      | [QuerySupplyRequest](collection.md#uptick.collection.v1.QuerySupplyRequest)           | [QuerySupplyResponse](collection.md#uptick.collection.v1.QuerySupplyResponse)           | Supply queries the total supply of a given denom or owner | GET       | /uptick/collection/collections/{denom_id}/supply |
| `NFTsOfOwner` | [QueryNFTsOfOwnerRequest](collection.md#uptick.collection.v1.QueryNFTsOfOwnerRequest) | [QueryNFTsOfOwnerResponse](collection.md#uptick.collection.v1.QueryNFTsOfOwnerResponse) | NFTsOfOwner queries the NFTs of the specified owner       | GET       | /uptick/collection/nfts                           |
| `Collection`  | [QueryCollectionRequest](collection.md#uptick.collection.v1.QueryCollectionRequest)   | [QueryCollectionResponse](collection.md#uptick.collection.v1.QueryCollectionResponse)   | Collection queries the NFTs of the specified denom        | GET       | /uptick/collection/collections/{denom_id}        |
| `Denom`       | [QueryDenomRequest](collection.md#uptick.collection.v1.QueryDenomRequest)             | [QueryDenomResponse](collection.md#uptick.collection.v1.QueryDenomResponse)             | Denom queries the definition of a given denom             | GET       | /uptick/collection/nft/denoms/{denom_id}         |
| `Denoms`      | [QueryDenomsRequest](collection.md#uptick.collection.v1.QueryDenomsRequest)           | [QueryDenomsResponse](collection.md#uptick.collection.v1.QueryDenomsResponse)           | Denoms queries all the denoms                             | GET       | /uptick/collection/nft/denoms                     |
| `NFT`         | [QueryNFTRequest](collection.md#uptick.collection.v1.QueryNFTRequest)                 | [QueryNFTResponse](collection.md#uptick.collection.v1.QueryNFTResponse)                 | NFT queries the NFT for the given denom and token ID      | GET       | /uptick/collection/nfts/{denom_id}/{token_id}   |



## uptick/collection/v1/tx.proto

### MsgBurnNFT

MsgBurnNFT defines an SDK message for burning a NFT.

| Field      | Type                           | Label | Description |
| ---------- | ------------------------------ | ----- | ----------- |
| `id`       | [string](value.md#string) |       |             |
| `denom_id` | [string](value.md#string) |       |             |
| `sender`   | [string](value.md#string) |       |             |

### MsgBurnNFTResponse

MsgBurnNFTResponse defines the Msg/BurnNFT response type.

### MsgEditNFT

MsgEditNFT defines an SDK message for editing a nft.

| Field      | Type                           | Label | Description |
| ---------- | ------------------------------ | ----- | ----------- |
| `id`       | [string](value.md#string) |       |             |
| `denom_id` | [string](value.md#string) |       |             |
| `name`     | [string](value.md#string) |       |             |
| `uri`      | [string](value.md#string) |       |             |
| `data`     | [string](value.md#string) |       |             |
| `sender`   | [string](value.md#string) |       |             |
| `uri_hash` | [string](value.md#string) |       |             |

### MsgEditNFTResponse

MsgEditNFTResponse defines the Msg/EditNFT response type.

### MsgIssueDenom

MsgIssueDenom defines an SDK message for creating a new denom.

| Field               | Type                           | Label | Description |
| ------------------- | ------------------------------ | ----- | ----------- |
| `id`                | [string](value.md#string) |       |             |
| `name`              | [string](value.md#string) |       |             |
| `schema`            | [string](value.md#string) |       |             |
| `sender`            | [string](value.md#string) |       |             |
| `symbol`            | [string](value.md#string) |       |             |
| `mint_restricted`   | [bool](value.md#bool)     |       |             |
| `update_restricted` | [bool](value.md#bool)     |       |             |
| `description`       | [string](value.md#string) |       |             |
| `uri`               | [string](value.md#string) |       |             |
| `uri_hash`          | [string](value.md#string) |       |             |
| `data`              | [string](value.md#string) |       |             |

### MsgIssueDenomResponse

MsgIssueDenomResponse defines the Msg/IssueDenom response type.

### MsgMintNFT

MsgMintNFT defines an SDK message for creating a new NFT.

| Field       | Type                           | Label | Description |
| ----------- | ------------------------------ | ----- | ----------- |
| `id`        | [string](value.md#string) |       |             |
| `denom_id`  | [string](value.md#string) |       |             |
| `name`      | [string](value.md#string) |       |             |
| `uri`       | [string](value.md#string) |       |             |
| `data`      | [string](value.md#string) |       |             |
| `sender`    | [string](value.md#string) |       |             |
| `recipient` | [string](value.md#string) |       |             |
| `uri_hash`  | [string](value.md#string) |       |             |

### MsgMintNFTResponse

MsgMintNFTResponse defines the Msg/MintNFT response type.

### MsgTransferDenom

MsgTransferDenom defines an SDK message for transferring an denom to recipient.

| Field       | Type                           | Label | Description |
| ----------- | ------------------------------ | ----- | ----------- |
| `id`        | [string](value.md#string) |       |             |
| `sender`    | [string](value.md#string) |       |             |
| `recipient` | [string](value.md#string) |       |             |

### MsgTransferDenomResponse

MsgTransferDenomResponse defines the Msg/TransferDenom response type.

### MsgTransferNFT

MsgTransferNFT defines an SDK message for transferring an NFT to recipient.

| Field       | Type                           | Label | Description |
| ----------- | ------------------------------ | ----- | ----------- |
| `id`        | [string](value.md#string) |       |             |
| `denom_id`  | [string](value.md#string) |       |             |
| `name`      | [string](value.md#string) |       |             |
| `uri`       | [string](value.md#string) |       |             |
| `data`      | [string](value.md#string) |       |             |
| `sender`    | [string](value.md#string) |       |             |
| `recipient` | [string](value.md#string) |       |             |
| `uri_hash`  | [string](value.md#string) |       |             |

### MsgTransferNFTResponse

MsgTransferNFTResponse defines the Msg/TransferNFT response type.

### Msg

Msg defines the nft Msg service.

| Method Name     | Request Type                                                            | Response Type                                                                           | Description                                              | HTTP Verb | Endpoint |
| --------------- | ----------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | -------------------------------------------------------- | --------- | -------- |
| `IssueDenom`    | [MsgIssueDenom](collection.md#uptick.collection.v1.MsgIssueDenom)       | [MsgIssueDenomResponse](collection.md#uptick.collection.v1.MsgIssueDenomResponse)       | IssueDenom defines a method for issue a denom.           |           |          |
| `MintNFT`       | [MsgMintNFT](collection.md#uptick.collection.v1.MsgMintNFT)             | [MsgMintNFTResponse](collection.md#uptick.collection.v1.MsgMintNFTResponse)             | MintNFT defines a method for mint a new nft              |           |          |
| `EditNFT`       | [MsgEditNFT](collection.md#uptick.collection.v1.MsgEditNFT)             | [MsgEditNFTResponse](collection.md#uptick.collection.v1.MsgEditNFTResponse)             | RefundHTLC defines a method for editing a nft.           |           |          |
| `TransferNFT`   | [MsgTransferNFT](collection.md#uptick.collection.v1.MsgTransferNFT)     | [MsgTransferNFTResponse](collection.md#uptick.collection.v1.MsgTransferNFTResponse)     | TransferNFT defines a method for transferring a nft.     |           |          |
| `BurnNFT`       | [MsgBurnNFT](collection.md#uptick.collection.v1.MsgBurnNFT)             | [MsgBurnNFTResponse](collection.md#uptick.collection.v1.MsgBurnNFTResponse)             | BurnNFT defines a method for burning a nft.              |           |          |
| `TransferDenom` | [MsgTransferDenom](collection.md#uptick.collection.v1.MsgTransferDenom) | [MsgTransferDenomResponse](collection.md#uptick.collection.v1.MsgTransferDenomResponse) | TransferDenom defines a method for transferring a denom. |           |          |

