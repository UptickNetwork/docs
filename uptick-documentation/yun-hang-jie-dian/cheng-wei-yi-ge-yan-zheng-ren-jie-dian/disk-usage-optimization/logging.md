# Logging

By default the logging level is set to `info`, and this produces a lot of logs. This log level might be good when starting up to see that the node starts syncing properly. However, after you see the syncing is going smoothly, you can lower the log level to `warn` (or `error`). On `config.toml` set the following

```Solidity
log_level = "warn"
```

Also ensure your log rotation is configured properly.
