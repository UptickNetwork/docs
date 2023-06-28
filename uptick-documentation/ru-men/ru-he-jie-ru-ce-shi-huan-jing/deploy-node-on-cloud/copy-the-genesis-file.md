# Copy the Genesis File

To connect the node to the existing testnet, fetch the testnet's `genesis.json` file and copy it into the new droplets config directory (i.e `$HOME/.uptickd/config/genesis.json`).

To do this ssh into both the testnet droplet and the new node droplet.

On your local machine copy the genesis.json file from the testnet droplet to the new droplet using:

```sh
scp -3 root@<TESTNET_IP_ADDRESS>:$HOME/.uptickd/config/genesis.json root@<NODE_IP_ADDRESS>:$HOME/.uptickd/config/genesis.json
```
