# State-sync snapshots

I believe this was disabled by default on Uptick, but listing it in any case here. On `app.toml` set

```Solidity
snapshot-interval = 0
```

Note that if state-sync was enabled on the network and working properly, it would allow one to sync a new node in few minutes. But this node would not have the history.
