# Fetch from a Trusted Source

If you are joining an existing testnet, you can fetch the genesis from the appropriate testnet source/repository where the genesis file is hosted.

Save the new genesis as `new_genesis.json`. Then, replace the old `genesis.json` with `new_genesis.json`.

```sh
cd $HOME/.uptickd/config
cp -f genesis.json new_genesis.json
mv new_genesis.json genesis.json
```
