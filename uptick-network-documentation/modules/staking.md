---
description: >-
  Staking module provides a set of subcommands to query staking state and send
  staking transactions.
---

# Staking

#### Available Commands

<table><thead><tr><th width="283">Name</th><th>Description</th></tr></thead><tbody><tr><td>validator</td><td>Query a validator</td></tr><tr><td>validators</td><td>Query for all validators</td></tr><tr><td>delegation</td><td>Query a delegation based on address and validator address</td></tr><tr><td>delegations</td><td>Query all delegations made from one delegator</td></tr><tr><td>delegations-to</td><td>Query all delegations to one validator</td></tr><tr><td>unbonding-delegation</td><td>Query an unbonding-delegation record based on delegator and validator address</td></tr><tr><td>unbonding-delegations</td><td>Query all unbonding-delegations records for one delegator</td></tr><tr><td>unbonding-delegations-from</td><td>Query all unbonding delegatations from a validator</td></tr><tr><td>redelegations-from</td><td>Query all outgoing redelegatations from a validator</td></tr><tr><td>redelegation</td><td>Query a redelegation record based on delegator and a source and destination validator address</td></tr><tr><td>redelegations</td><td>Query all redelegations records for one delegator</td></tr><tr><td>pool</td><td>Query the current staking pool values</td></tr><tr><td>params</td><td>Query the current staking parameters information</td></tr><tr><td>historical-info</td><td>Query historical info at given height</td></tr><tr><td>create-validator</td><td>Create new validator initialized with a self-delegation to it</td></tr><tr><td>edit-validator</td><td>Edit existing validator account</td></tr><tr><td>delegate</td><td>Delegate liquid tokens to an validator</td></tr><tr><td>unbond</td><td>Unbond shares from a validator</td></tr><tr><td>redelegate</td><td>Redelegate illiquid tokens from one validator to another</td></tr></tbody></table>

#### uptickd query staking validator

Query a validator by validator address

```Bash
uptickd query staking validator [validator-addr] [flags]
```

#### uptickd query staking validators

Query all validators

```Bash
uptickd query staking validators
```

#### uptickd query staking delegation

Query a delegation based on delegator address and validator address.

```Bash
uptickd query staking delegation [delegator-addr] [validator-addr] [flags]
```

Query a delegation

```Bash
uptickd query staking delegation <uptick...> <uptickvaloper...>
```

Example Output:

```Bash
Delegation:
  Delegator:  uptick1e7v3fn2yxxlzpmlgy9232neykpe57gzupas6z6
  Validator:  uptickvaloper1a3ep09wd27c7av77z90a6l5mlh58unk8qdtw5v
  Shares:     1.0000000000000000000000000000
  Height:     26

```

#### uptickd query staking delegations

Query all delegations delegated from one delegator.

```Bash
uptickd query staking delegations [delegator-addr] [flags]
```

Query all delegations of a delegator

```Bash
uptickd query staking delegations <uptick...>
```

#### uptickd query staking delegations-to

Query all delegations to one validator.

```Bash
uptickd query staking delegations-to [validator-addr] [flags]
```

Query all delegations to one validator

```Bash
uptickd query staking delegations-to <uptickvaloper...>
```

Example Output:

```Python
delegation_responses:
- balance:
    amount: "1000000000000000000"
    denom: auoc
  delegation:
    delegator_address: uptick1ehh5503n2rhpz8evfqpsa62kfqc58c5g02kjhd
    shares: "1000000000000000000.000000000000000000"
    validator_address: uptickvaloper1a3ep09wd27c7av77z90a6l5mlh58unk8qdtw5v
- balance:
    amount: "300000000000000000000000000"
    denom: auoc
  delegation:
    delegator_address: uptick1a3ep09wd27c7av77z90a6l5mlh58unk8n476cq
    shares: "300000000000000000000000000.000000000000000000"
    validator_address: uptickvaloper1a3ep09wd27c7av77z90a6l5mlh58unk8qdtw5v
pagination:
  next_key: null
  total: "0"
```

#### uptickd query staking unbonding-delegation

Query an unbonding-delegation record based on delegator and validator address.

```Bash
uptickd query staking unbonding-delegation [delegator-addr] [validator-addr] [flags]
```

Query an unbonding delegation record

```Bash
uptickd query staking unbonding-delegation <uptick...> <uptickvaloper...>
```

#### uptickd query staking unbonding-delegations

Query all unbonding delegations records of a delegator

```Bash
uptickd query staking unbonding-delegations [delegator-addr] [flags]
```

#### uptickd query staking unbonding-delegations-from

Query all unbonding delegations from a validator

```Bash
uptickd query staking unbonding-delegations-from [validator-addr] [flags]
```

#### uptickd query staking redelegations-from

Query all outgoing redelegations of a validator

```Bash
uptickd query staking redelegations-from [validator-addr] [flags]
```

Query all outgoing redelegatations of a validator

```Bash
uptickd query staking redelegations-from <uptickvaloper...>
```

#### uptickd query staking redelegation

Query a redelegation record based on delegator and source validator address and destination validator address.

```Bash
uptickd query staking redelegation [delegator-addr] [src-validator-addr] [dst-validator-addr] [flags]
```

Query a redelegation record

```Bash
uptickd query staking redelegation <uptick...> <uptickvaloper...> <uptickvaloper...>
```

#### uptickd query staking redelegations

Query all redelegations records of a delegator

```Bash
uptickd query staking redelegations [delegator-addr] [flags]
```

#### uptickd query staking pool

Query the current staking pool values

```Bash
uptickd query staking pool
```

Example Output:

```Bash
bonded_tokens: "300000001000000000000000000"
not_bonded_tokens: "0"
```

#### uptickd query staking params

Query the current staking parameters information

```Bash
uptickd query staking params
```

#### uptickd query staking historical-info

Query historical info at given height

```Bash
uptickd query staking historical-info [height] [flags]
```

#### uptickd tx staking create-validator

Send a transaction to apply to be a validator and delegate a certain amount of iris to it.

```Bash
uptickd tx staking create-validator [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="144">type</th><th width="119">Required</th><th width="109">Default</th><th>Description</th></tr></thead><tbody><tr><td>--amount</td><td>string</td><td>Yes</td><td></td><td>Amount of coins to bond</td></tr><tr><td>--commission-rate</td><td>float</td><td>Yes</td><td>0</td><td>The initial commission rate percentage</td></tr><tr><td>--commission-max-rate</td><td>float</td><td></td><td>0</td><td>The maximum commission rate percentage</td></tr><tr><td>--commission-max-change-rate</td><td>float</td><td></td><td>0</td><td>The maximum commission change rate percentage (per day)</td></tr><tr><td>--min-self-delegation</td><td>string</td><td></td><td></td><td>The minimum self delegation required on the validator</td></tr><tr><td>--details</td><td>string</td><td></td><td></td><td>Optional details</td></tr><tr><td>--genesis-format</td><td>bool</td><td></td><td>FALSE</td><td>Export the transaction in gen-tx format; it implies --generate-only</td></tr><tr><td>--identity</td><td>string</td><td></td><td></td><td>Optional identity signature (ex. UPort or Keybase)</td></tr><tr><td>--ip</td><td>string</td><td></td><td></td><td>Node's public IP. It takes effect only when used in combination with</td></tr><tr><td>--node-id</td><td>string</td><td></td><td></td><td>The node's ID</td></tr><tr><td>--moniker</td><td>string</td><td>Yes</td><td></td><td>Validator name</td></tr><tr><td>--pubkey</td><td>string</td><td>Yes</td><td></td><td>Go-Amino encoded hex PubKey of the validator. For Ed25519 the go-amino prepend hex is 1624de6220</td></tr><tr><td>--website</td><td>string</td><td></td><td></td><td>Optional website</td></tr><tr><td>--security-contact</td><td>string</td><td></td><td></td><td>The validator's (optional) security contact email</td></tr></tbody></table>

Create a validator

```Python
uptickd tx staking create-validator --chain-id=<chain-id> --from=<key-name> --fees=0.3uptick --pubkey=<validator-pubKey> --commission-rate=0.1 --amount=100uptick --moniker=<validator-name>
```

> TIPFollow the Mainnet instructions to learn more.

#### uptickd tx staking edit-validator

Edit an existing validator's settings, such as commission rate, name, etc.

```Bash
uptickd tx staking edit-validator [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="94">type</th><th width="102">Required</th><th width="108">Default</th><th>Description</th></tr></thead><tbody><tr><td>--commission-rate</td><td>float</td><td></td><td>0</td><td>Commission rate percentage</td></tr><tr><td>--moniker</td><td>string</td><td></td><td></td><td>Validator name</td></tr><tr><td>--identity</td><td>string</td><td></td><td></td><td>Optional identity signature (ex. UPort or Keybase)</td></tr><tr><td>--website</td><td>string</td><td></td><td></td><td>Optional website</td></tr><tr><td>--details</td><td>string</td><td></td><td></td><td>Optional details</td></tr><tr><td>--security-contact</td><td>string</td><td></td><td></td><td>The validator's (optional) security contact email</td></tr><tr><td>--min-self-delegation</td><td>string</td><td></td><td></td><td>The minimum self delegation required on the validator</td></tr></tbody></table>

Edit validator information

```Bash
uptickd tx staking edit-validator --from=<key-name> --chain-id=<chain-id> --fees=0.3uptick --commission-rate=0.10 --moniker=<validator-name>
```

Upload validator avatarPlease refer to How to upload my validator's logo to the Explorers

#### uptickd tx staking delegate

Delegate tokens to a validator.

```Bash
uptickd tx staking delegate [validator-addr] [amount] [flags]
```

#### uptickd tx staking unbond

Unbond tokens from a validator.

```Bash
uptickd tx staking unbond [validator-addr] [amount] [flags]
```

#### uptickd tx staking redelegate

Transfer delegation from one validator to another.

> **TIP**
>
> There is no `unbonding time` during the redelegation, so you will not miss the rewards. But you can only redelegate once per validator, until a period (= `unbonding time`) exceed.

```Bash
uptickd tx staking redelegate [src-validator-addr] [dst-validator-addr] [amount] [flags]
```
