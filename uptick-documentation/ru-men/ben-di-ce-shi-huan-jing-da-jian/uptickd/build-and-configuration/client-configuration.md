# Client configuration

We can view the default client config setting by using `uptickd config` command:

```sh
uptickd config
{
 "chain-id": "",
 "keyring-backend": "os",
 "output": "text",
 "node": "tcp://localhost:26657",
 "broadcast-mode": "sync"
}
```

We can make changes to the default settings upon our choices, so it allows users to set the configuration beforehand all at once, so it would be ready with the same config afterward.

For example, the chain identifier can be changed to `uptick_7000-2` from a blank name by using:

```sh
uptickd config "chain-id" uptick_7000-2
uptickd config
{
 "chain-id": "uptick_7000-2",
 "keyring-backend": "os",
 "output": "text",
 "node": "tcp://localhost:26657",
 "broadcast-mode": "sync"
}
```

Other values can be changed in the same way.

Alternatively, we can directly make the changes to the config values in one place at client.toml. It is under the path of `.uptick/config/client.toml` in the folder where we installed uptick:

```sh
############################################################################
### Client Configuration ###

############################################################################

# The network chain ID

chain-id = "uptick_7000-2"

# The keyring's backend, where the keys are stored (os|file|kwallet|pass|test|memory)

keyring-backend = "os"

# CLI output format (text|json)

output = "number"

# <host>:<port> to Tendermint RPC interface for this chain

node = "tcp://localhost:26657"

# Transaction broadcasting mode (sync|async|block)

broadcast-mode = "sync"
```

After the necessary changes are made in the `client.toml`, then save. For example, if we directly change the chain-id from `uptick_7000-2` to `upticktest_7000-1`, and output to number, it would change instantly as shown below.

```sh
uptickd config
{
 "chain-id": "upticktest_7000-1",
 "keyring-backend": "os",
 "output": "number",
 "node": "tcp://localhost:26657",
 "broadcast-mode": "sync"
}
```
