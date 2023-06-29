# Introduction

`uptickd` is a command line client for the Uptick network. Uptick users can use `uptickd` to send transactions and query
the blockchain data.

# Working Directory

The default working directory for the `uptickd` is `$HOME/.uptickd`, which is mainly used to save configuration files
and data. The ptick `key` data is saved in the working directory of `uptickd`. You can also specify the `uptickd`
working directory by `--home`.

# Connecting to a Full Node

The `uptickd` node provides a RPC interface, transactions and query requests are sent to the process listening to it.
The default rpc address the `uptickd` is connected to is `tcp://localhost:26657`. It can also be specified by `--node`.

# GET Commands

All GET commands has the following global flags:

| Name, shorthand | type   | Required | Default Value         | Description                          |
| --------------- | ------ | -------- | --------------------- | ------------------------------------ |
| --chain-id      | string |          | testnet               | Specify Chain ID for sending Tx      |
| --home          | string |          | /Users/xxxxx/.uptickd | Directory for config and data        |
| --trace         | string |          |                       | Print out full stack trace on errors |

# POST Commands

All POST commands have the following global flags:

| Name, shorthand   | type   | Required | Default               | Description                                                                                                    |
| ----------------- | ------ | -------- | --------------------- | -------------------------------------------------------------------------------------------------------------- |
| --account-number  | int    |          | 0                     | AccountNumber to sign the tx                                                                                   |
| --broadcast-mode  | string |          | sync                  | Transaction broadcasting mode (sync | async | block)                                                         |
| --dry-run         | bool   |          | false                 | Ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it                        |
| --fees            | string |          |                       | Fees to pay along with transaction                                                                             |
| --from            | string |          |                       | Name of private key with which to sign                                                                         |
| --gas             | string |          | 40000                 | Gas limit to set per-transaction; set to "simulate" to calculate required gas automatically                    |
| --gas-adjustment  | float  |          | 1                     | Adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set |
| --gas-prices      | string |          |                       | Gas prices in decimal format to determine the transaction fee                                                  |
| --generate-only   | bool   |          | false                 | Build an unsigned transaction and write it to STDOUT                                                           |
| --help, -h        | string |          |                       | Print help message                                                                                             |
| --keyring-backend | string |          | os                    | Select keyring's backend                                                                                       |
| --ledger          | bool   |          | false                 | Use a connected Ledger device                                                                                  |
| --memo            | string |          |                       | Memo to send along with transaction                                                                            |
| --node            | string |          | tcp://localhost:26657 | <host>:<port> to tendermint rpc interface for this chain                                                     |
| --offline         | string |          |                       | Offline mode (does not allow any online functionality)                                                         |
| --sequence        | int    |          | 0                     | Sequence number to sign the tx                                                                                 |
| --sign-mode       | string |          |                       | Choose sign mode (direct | amino-json), this is an advanced feature                                           |
| --trust-node      | bool   |          | true                  | Don't verify proofs for responses                                                                              |
| --yes             | bool   |          | true                  | Skip tx broadcasting prompt confirmation                                                                       |
| --chain-id        | string |          |                       | Chain ID of tendermint node                                                                                    |
| --home            | string |          |                       | Directory for config and data (default "$HOME/.uptick")                                                 |
| --trace           | string |          |                       | Print out full stack trace on errors


# Module Commands

| Subcommand          | Description                                                                            |
| ------------------- | -------------------------------------------------------------------------------------- |
| add-genesis-account | Add a genesis account to genesis.json                                                  |
| collect-gentxs      | Collect genesis txs and output a genesis.json file                                     |
| config              | Create or query an application CLI configuration file                                  |
| debug               | Tool for helping with debugging your application                                       |
| export              | Export state to JSON                                                                   |
| gentx               | Generate a genesis tx carrying a self delegation                                       |
| help                | Help about any command                                                                 |
| index-eth-tx        | Index historical eth txs                                                               |
| init                | Initialize private validator, p2p, genesis, and application configuration files        |
| keys                | Manage your application's keys                                                         |
| migrate             | Migrate genesis to a specified target version                                          |
| query               | Querying subcommands                                                                   |
| rollback            | rollback cosmos-sdk and tendermint state by one height                                 |
| rosetta             | spin up a rosetta server                                                               |
| start               | Run the full node                                                                      |
| status              | Query remote node for status                                                           |
| tendermint          | Tendermint subcommands                                                                 |
| testnet             | subcommands for starting or configuring local testnets                                 |
| tx                  | Transactions subcommands                                                               |
| validate-genesis    | validates the genesis file at the default location or at the location passed as an arg |
| version             | Print the application binary version information                                       |
