# Download Genesis File

You can now download the "genesis" file for the chain. It is pre-filled with the entire genesis state and gentxs.

```sh
curl https://raw.githubusercontent.com/UptickNetwork/uptick-testnet/main/uptick_7000-2/genesis.json > ~/.uptickd/config/genesis.json
```

We recommend using `sha256sum` to check the hash of the genesis.

```sh
cd ~/.uptickd/config
echo "2b5164f4bab00263cb424c3d0aa5c47a707184c6ff288322acc4c7e0c5f6f36f  genesis.json" | sha256sum -c
```
