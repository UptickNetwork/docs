---
description: The distribution module allows you to manage your Staking Rewards.
---

# Distribution

#### Available Subcommands

<table><thead><tr><th width="286">Name</th><th>Description</th></tr></thead><tbody><tr><td>commission</td><td>Query distribution validator commission</td></tr><tr><td>community-pool</td><td>Query the amount of coins in the community pool</td></tr><tr><td>params</td><td>Query distribution params</td></tr><tr><td>rewards</td><td>Query all distribution delegator rewards or rewards from a particular validator</td></tr><tr><td>slashes</td><td>Query distribution validator slashes</td></tr><tr><td>validator-outstanding-rewards</td><td>Query distribution outstanding (un-withdrawn) rewards for a validator and all their delegations</td></tr><tr><td>fund-community-pool</td><td>Funds the community pool with the specified amount</td></tr><tr><td>set-withdraw-addr</td><td>Set the withdraw address for rewards associated with a delegator address</td></tr><tr><td>withdraw-all-rewards</td><td>Withdraw all rewards for a single delegator</td></tr><tr><td>withdraw-rewards</td><td>Withdraw rewards from a given delegation address,and optionally withdraw validator commission if the delegation address given is a validator operator</td></tr></tbody></table>

#### uptickd query distribution commission

Query validator commission rewards from delegators to that validator.

```Bash
uptickd query distribution commission [validator] [flags]
```

#### uptickd query distribution community-pool

Query all coins in the community pool which is under Governance control.

```Bash
uptickd query distribution community-pool [flags]
```

#### uptickd query distribution params

Query distribution params.

```Bash
uptickd query distribution params [flags]
```

#### uptickd query distribution rewards

Query all rewards earned by a delegator, optionally restrict to rewards from a single validator.

```Bash
uptickd query distribution rewards [delegator-addr] [validator-addr] [flags]
```

#### uptickd query distribution slashes

Query all slashes of a validator for a given block range.

```Bash
uptickd query distribution slashes [validator] [start-height] [end-height] [flags]
```

#### uptickd query distribution validator-outstanding-rewards

Query distribution outstanding (un-withdrawn) rewards for a validator and all their delegations.

```Bash
uptickd query distribution validator-outstanding-rewards [validator] [flags]
```

#### uptickd tx distribution fund-community-pool

Funds the community pool with the specified amount.

```Bash
uptickd tx distribution fund-community-pool [amount] [flags]
```

#### uptickd tx distribution set-withdraw-addr

Set the withdraw address for rewards associated with a delegator address.

```Bash
uptickd tx distribution set-withdraw-addr [withdraw-addr] [flags]
```

#### uptickd tx distribution withdraw-all-rewards

Withdraw all rewards for a single delegator.

```Bash
uptickd tx distribution withdraw-all-rewards [flags]
```

#### uptickd tx distribution withdraw-rewards

Withdraw rewards from a given delegation address, and optionally withdraw validator commission if the delegation address given is a validator operator.

```Bash
uptickd tx distribution withdraw-rewards [validator-addr] [flags]
```
