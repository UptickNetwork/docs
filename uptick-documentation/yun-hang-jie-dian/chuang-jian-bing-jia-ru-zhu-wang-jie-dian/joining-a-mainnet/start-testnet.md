# Start testnet

The final step is to [start the nodes](https://docs.uptick.network/quickstart/run_node#start-node). Once enough voting power (+2/3) from the genesis validators is up-and-running, the testnet will start producing blocks.

```sh
# start the node (you can also use "nohup" or "systemd" to run in the background)
uptickd start
```

{% hint style="info" %}
You may see some connection errors, it does not matter, the P2P network is trying to find available connections

Try to add some of the [Community Peers ](https://github.com/UptickNetwork/uptick-mainnet/tree/main/uptick_117-1)to persistent_peers in the config.toml

If you want to quickly start the node and join Uptick without historical data, you can consider using the [state_sync](https://docs.uptick.network/guides/statesync/statesync.html) function.
{% endhint %}
