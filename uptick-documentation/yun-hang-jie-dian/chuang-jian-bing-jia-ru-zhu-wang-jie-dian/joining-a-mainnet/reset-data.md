# Reset Data

{% hint style="info" %}
If the version <new_version> you are upgrading to is not breaking from the previous one, you **should not** reset the data. If this is the case you can skip to [Restart](https://docs.uptick.network/mainnet/join.html#restart)
{% endhint %}

First, remove the outdated files and reset the data.

```sh
rm $HOME/.uptickd/config/addrbook.json $HOME/.uptickd/config/genesis.json
uptickd tendermint unsafe-reset-all
```

Your node is now in a pristine state while keeping the original `priv_validator.json` and `config.toml`. If you had any sentry nodes or full nodes setup before, your node will still try to connect to them, but may fail if they haven't also been upgraded.

{% hint style="info" %}
Warning

Make sure that every node has a unique `priv_validator.json`. Do not copy the `priv_validator.json` from an old node to multiple new nodes. Running two nodes with the same `priv_validator.json` will cause you to double sign.
{% endhint %}
