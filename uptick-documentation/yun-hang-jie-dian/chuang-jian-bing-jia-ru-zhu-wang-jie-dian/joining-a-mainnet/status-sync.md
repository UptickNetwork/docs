# Status Sync

To quickly get started, node operators can choose to sync via State Sync. State Sync works by replaying larger chunks of application state directly rather than replaying individual blocks or consensus rounds.

The newest state sync configs can be found [here](https://explorer.uptick.network/uptick-network-mainnet/statesync). Please remember to modify state sync configs.

```sh
# initialize node configurations
uptickd init <moniker> --chain-id uptick_117-1

# download testnel public genesis.json
curl -o $HOME/.uptickd/config/genesis.json https://raw.githubusercontent.com/UptickNetwork/uptick-mainnet/master/uptick_117-1/genesis.json

# Configure State sync
[statesync]
enable = true
rpc_servers = "http://18.138.220.30:26657,http://18.141.43.191:26657"
trust_height = 12000
trust_hash = "dee636061e072ba3e0fee408718b7aff97bd8d4a2a27c695c8d4c8b87081d698"
trust_period = "168h"  # 2/3 of unbonding time

# start the node (you can also use "nohup" or "systemd" to run in the background)
uptickd start
```
