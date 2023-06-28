# Joining a Mainnet

This document outlines the steps to join an existing mainnet

## Pick a Testnet

You specify the network you want to join by setting the **genesis file** and **seeds**. If you need more information about past networks, check our [mainnet repo](https://github.com/UptickNetwork/uptick-mainnet).

| Network Chain ID | Description    | Site                                                                                     | Version                                                         |
| ---------------- | -------------- | ---------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| `uptick_117-1`   | Uptick mainnet | [uptick\_117-1](https://github.com/UptickNetwork/uptick-mainnet/tree/main/uptick\_117-1) | [`v0.2.4`](https://github.com/UptickNetwork/uptick/tree/v0.2.4) |

## Install `uptickd`

Follow the [installation](https://github.com/starrymedia/upticknetworkdocs/blob/main/quickstart/installation/README.md) document to install the Uptick binary `uptickd`.

warning Make sure you have the right version of `uptickd` installed.

### Save Chain ID

We recommend saving the mainnet `chain-id` into your `uptickd`'s `client.toml`. This will make it so you do not have to manually pass in the `chain-id` flag for every CLI command.

{% hint style="info" %}
See the Official [Chain IDs](../concepts/basics/chain\_id.md#official-chain-ids) for reference.
{% endhint %}

```bash
uptickd config chain-id uptick_117-1
```

## Initialize Node

We need to initialize the node to create all the necessary validator and node configuration files:

```bash
# initialize node configurations
uptickd init <moniker> --chain-id uptick_117-1

# download testnel public genesis.json
curl -o $HOME/.uptickd/config/genesis.json https://raw.githubusercontent.com/UptickNetwork/uptick-mainnet/master/uptick_117-1/genesis.json

```

## Start testnet

The final step is to [start the nodes](https://github.com/starrymedia/upticknetworkdocs/blob/main/quickstart/run\_node/README.md#start-node). Once enough voting power (+2/3) from the genesis validators is up-and-running, the testnet will start producing blocks.

```bash
# start the node (you can also use "nohup" or "systemd" to run in the background)
uptickd start
```

{% hint style="info" %}
You may see some connection errors, it does not matter, the P2P network is trying to find available connections

Try to add some of the [Community Peers](https://github.com/UptickNetwork/uptick-mainnet/tree/main/uptick\_117-1) to persistent\_peers in the config.toml

If you want to quickly start the node and join Uptick without historical data, you can consider using the [state\_sync](../guides/statesync.md) function.
{% endhint %}

## Status Sync

To quickly get started, node operators can choose to sync via State Sync. State Sync works by replaying larger chunks of application state directly rather than replaying individual blocks or consensus rounds.

The newest state sync configs can be found [here](https://explorer.uptick.network/uptick-network-mainnet/statesync). Please remember to modify state sync configs.

```bash
# initialize node configurations
uptickd init <moniker> --chain-id uptick_117-1

# download testnel public genesis.json
curl -o $HOME/.uptickd/config/genesis.json https://raw.githubusercontent.com/UptickNetwork/uptick-mainnet/master/uptick_117-1/genesis.json

# Configure State sync
[statesync]
enable = true
rpc_servers = "https://rpc.uptick.nodestake.top:443,https://rpc.uptick.nodestake.top:443"
trust_height = 12000
trust_hash = "dee636061e072ba3e0fee408718b7aff97bd8d4a2a27c695c8d4c8b87081d698"
trust_period = "168h"  # 2/3 of unbonding time

# start the node (you can also use "nohup" or "systemd" to run in the background)
uptickd start
```

## Run a Validator

Confirm your node has caught-up

```bash
# if you have not installed jq
# apt-get update && apt-get install -y jq

# if the output is false, means your node has caught-up
uptickd status | jq .sync_info.catching_up
```

{% hint style="info" %}
For more details on how to configure your validator, follow the validator [setup](../guides/validators/setup.md) instructions.
{% endhint %}

```bash
uptickd tx staking create-validator \
  --amount=5000000000000000000auptick \
  --chain-id=uptick_117-1 \
  --commission-rate="0.10" \
  --commission-max-rate="0.20" \
  --commission-max-change-rate="0.01" \
  --min-self-delegation="1000000" \
  --moniker="moniker" \
  --identity="identity" \
  --website="website" \
  --details="details" \
  --from=<$Validator wallet name> \
  -y -b block
```

## Upgrading Your Node

> NOTE: These instructions are for full nodes that have ran on previous versions of and would like to upgrade to the latest testnet.

### Reset Data

warning If the version \<new\_version> you are upgrading to is not breaking from the previous one, you **should not** reset the data. If this is the case you can skip to [Restart](join.md#restart)

First, remove the outdated files and reset the data.

```bash
rm $HOME/.uptickd/config/addrbook.json $HOME/.uptickd/config/genesis.json
uptickd tendermint unsafe-reset-all
```

Your node is now in a pristine state while keeping the original `priv_validator.json` and `config.toml`. If you had any sentry nodes or full nodes setup before, your node will still try to connect to them, but may fail if they haven't also been upgraded.

{% hint style="info" %}
Warning Make sure that every node has a unique `priv_validator.json`. Do not copy the `priv_validator.json` from an old node to multiple new nodes. Running two nodes with the same `priv_validator.json` will cause you to double sign.
{% endhint %}

### Restart

To restart your node, just type:

```bash
uptickd start
```

### State Syncing a Node

If you want to join the network using State Sync (quick, but not applicable for archive nodes), check our [State Sync](../guides/statesync.md#State-Sync)page
