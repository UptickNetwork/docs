# Initialize Node

We need to initialize the node to create all the necessary validator and node configuration files:

```sh
# initialize node configurations
uptickd init <moniker> --chain-id uptick_117-1

# download testnel public genesis.json
curl -o $HOME/.uptickd/config/genesis.json https://raw.githubusercontent.com/UptickNetwork/uptick-mainnet/master/uptick_117-1/genesis.json

```
