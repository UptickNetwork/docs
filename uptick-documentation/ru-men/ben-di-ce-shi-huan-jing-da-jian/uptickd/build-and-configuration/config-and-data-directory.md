# Config and data directory

By default, your config and data are stored in the folder located at the `~/.uptickd` directory.

```
.                                   # ~/.uptickd
  ├── data/                           # Contains the databases used by the node.
  └── config/
      ├── app.toml                   # Application-related configuration file.
      ├── config.toml                # Tendermint-related configuration file.
      ├── genesis.json               # The genesis file.
      ├── node_key.json              # Private key to use for node authentication in the p2p protocol.
      └── priv_validator_key.json    # Private key to use as a validator in the consensus protocol.
```

To specify the `uptickd` config and data storage directory; you can update it using the global flag `--home <directory>`
