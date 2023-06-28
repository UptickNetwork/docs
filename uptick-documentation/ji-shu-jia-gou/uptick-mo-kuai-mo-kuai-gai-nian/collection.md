# Collection

`Collection` provides the ability to digitize assets. Through this module, each off-chain asset will be modeled as a unique on-chain nft.

#### Available Commands

<table><thead><tr><th width="227">Name</th><th>Description</th></tr></thead><tbody><tr><td>issue</td><td>Specify the nft Denom (nft classification) and metadata JSON Schema to issue nft.</td></tr><tr><td>transfer-denom</td><td>The owner of the NFT classification can transfer the ownership of the NFT classification to others.</td></tr><tr><td>mint</td><td>Additional issuance (create) of specific nft of this type can be made.</td></tr><tr><td>edit</td><td>The metadata of the specified nft can be updated.</td></tr><tr><td>transfer</td><td>Transfer designated nft.</td></tr><tr><td>burn</td><td>Destroy the created nft.</td></tr></tbody></table>

#### uptickd tx collection issue

Specify the nft Denom (nft classification) and metadata JSON Schema to issue nft.

```Bash
uptickd tx collection issue [denom-id] [flags]
```

Flags:

<table><thead><tr><th width="147">Name, shorthand</th><th width="104">Required</th><th>Default</th><th width="373">Description</th></tr></thead><tbody><tr><td>--name</td><td></td><td></td><td>The name of the denom</td></tr><tr><td>--uri</td><td></td><td></td><td>The uri of the denom</td></tr><tr><td>--data</td><td></td><td></td><td>Off-chain metadata for supplementation (JSON object)</td></tr><tr><td>--schema</td><td></td><td></td><td>Denom data structure definition</td></tr><tr><td>--symbol</td><td></td><td></td><td>The symbol of the denom</td></tr><tr><td>--mint-restricted</td><td></td><td></td><td>This field indicates whether there are restrictions on the issuance of NFTs under this classification, true means that only Denom owners can issue NFTs under this classification, false means anyone can</td></tr><tr><td>--update-restricted</td><td></td><td></td><td>This field indicates whether there are restrictions on updating NFTs under this classification, true means that no one under this classification can update the NFT, false means that only the owner of this NFT can update</td></tr></tbody></table>

#### uptickd tx collection transfer-denom

The owner of the NFT classification can transfer the ownership of the NFT classification to others.

```Bash
uptickd tx collection transfer-denom [recipient] [denom-id] [flags]
```

#### uptickd tx collection mint

Additional issuance (create) of specific nft of this type can be made.

```Bash
uptickd tx collection mint [denom-id] [nft-id] [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th>Required</th><th width="122">Default</th><th>Description</th></tr></thead><tbody><tr><td>--uri</td><td></td><td></td><td>URI of off-chain token data</td></tr><tr><td>--recipient</td><td></td><td></td><td>Receiver of the nft</td></tr><tr><td>--name</td><td></td><td></td><td>The name of nft</td></tr></tbody></table>

#### uptickd tx collection edit

The metadata of the specified nft can be updated.

```Bash
uptickd tx collection edit [denom-id] [nft-id] [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="98">Required</th><th width="108">Default</th><th>Description</th></tr></thead><tbody><tr><td>--uri</td><td></td><td></td><td>URI of off-chain token data</td></tr><tr><td>--name</td><td></td><td></td><td>The name of nft</td></tr></tbody></table>

#### uptickd tx collection transfer

Transfer designated nft.

```Bash
 uptickd tx collection transfer [recipient] [denom-id] [nft-id] [flags]
```

Flags:

| Name, shorthand | Required | Default | Description                 |
| --------------- | -------- | ------- | --------------------------- |
| --uri           |          |         | URI of off-chain token data |

#### uptickd tx collection burn

Destroy the created nft.

```Bash
uptickd tx collection burn [denom-id] [nft-id] [flags]
```

#### uptickd query collection

Query nft

#### uptickd query collection supply

```Bash
uptickd query collection supply [denom-id] [flags]
```

#### uptickd query collection owner

```Bash
 uptickd query collection owner [address] [flags]
```

#### uptickd query collection collection

```Bash
uptickd query collection collection [denom-id] [flags]
```

#### uptickd query collection denom

```Bash
uptickd query collection denom [denom-id] [flags]
```

#### uptickd query collection denoms

```Bash
uptickd query collection denoms
```

#### uptickd query collection token

```Bash
uptickd query collection token [denom-id] [nft-id] [flags]
```
