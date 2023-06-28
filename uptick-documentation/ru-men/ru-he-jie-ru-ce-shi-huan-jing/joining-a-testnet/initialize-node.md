# Initialize Node

We need to initialize the node to create all the necessary validator and node configuration files:

```Shell
# initialize node configurations
uptickd init <your_custom_moniker> --chain-id uptick_7000-2

# download testnel public genesis.json
curl -o $HOME/.uptickd/config/genesis.json https://raw.githubusercontent.com/UptickNetwork/uptick-testnet/main/uptick_7000-2/genesis.json
```
