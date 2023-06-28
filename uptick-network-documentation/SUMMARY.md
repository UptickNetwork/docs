# Table of contents

* [Reference](README.md)
  * [Introduction](readme/intro/README.md)
    * [High-level Overview](readme/intro/overview.md)
    * [Architecture](readme/intro/architecture.md)
    * [Clients](readme/intro/clients.md)
    * [Use Cases](readme/intro/use\_cases.md)
    * [resources](readme/intro/resources.md)
  * [QuickStart](readme/quickstart/README.md)
    * [Installation](readme/quickstart/installation.md)
    * [uptickd](readme/quickstart/binary.md)
    * [Deterministic Builds](readme/quickstart/reproducible-builds.md)
    * [Run a Node](readme/quickstart/run\_node.md)
    * [Interacting with the Node](readme/quickstart/interact\_node.md)
    * [Cosmovisor](readme/quickstart/cosmovisor.md)
  * [Basics](readme/basics/README.md)
    * [Chain ID](readme/basics/chain\_id.md)
    * [Accounts](readme/basics/accounts.md)
    * [Transaction Lifecycle](readme/basics/transactions.md)
    * [Gas and Fees](readme/basics/gas.md)
    * [Tokens](readme/basics/tokens.md)
  * [Core Concepts](readme/core/README.md)
    * [Encoding](readme/core/encoding.md)
    * [Pending State](readme/core/pending\_state.md)
* [Guides](guides/README.md)
  * [Localnet](guides/localnet/README.md)
    * [Single Node](guides/localnet/single\_node.md)
    * [Multi Node](guides/localnet/multi\_node.md)
    * [Testnet command](guides/localnet/testnet\_cmd.md)
  * [keys-wallets](guides/keys-wallets/README.md)
    * [keyring](guides/keys-wallets/keyring.md)
    * [MetaMask](guides/keys-wallets/metamask.md)
    * [Multisig](guides/keys-wallets/multisig.md)
    * [Keplr](guides/keys-wallets/keplr.md)
  * [Ethereum Tooling](guides/tools/README.md)
    * [Remix: Deploying a Smart Contract](guides/tools/remix.md)
    * [Hardhat: Deploying a Smart Contract](guides/tools/hardhat.md)
    * [Truffle: Deploying a Smart Contract](guides/tools/truffle.md)
  * [Validators](guides/validators/README.md)
    * [Overview](guides/validators/overview.md)
    * [Run a Validator](guides/validators/setup.md)
    * [Validator Security](guides/validators/security.md)
    * [Validator Security Checklist](guides/validators/checklist.md)
    * [Validator FAQ](guides/validators/faq.md)
    * [Disk Usage Optimization](guides/validators/disk\_optimization.md)
  * [Key Management System](guides/kms/README.md)
    * [Tendermint KMS](guides/kms/kms.md)
  * [State Sync](guides/statesync.md)
* [API](api/README.md)
  * [JSON-RPC Server](api/json-rpc/README.md)
    * [JSON-RPC Server](api/json-rpc/server.md)
    * [Running the Server](api/json-rpc/running\_server.md)
    * [Namespaces](api/json-rpc/namespaces.md)
    * [JSON-RPC Methods](api/json-rpc/endpoints.md)
    * [events](api/json-rpc/events.md)
  * [sdk](api/sdk.md)
  * [Protobuf Documentation](api/proto-docs.md)
* [MAINNET](mainnet/README.md)
  * [Joining a Mainnet](mainnet/join.md)
  * [Block Explorers](mainnet/explorer.md)
* [TESTNET](testnet/README.md)
  * [Joining a Testnet](testnet/join.md)
  * [Testnet Faucet](testnet/faucet.md)
  * [Block Explorers](testnet/explorer.md)
  * [Deploy Node on Cloud](testnet/cloud\_providers.md)
* [Specifications](specifications/README.md)
  * [Modules](specifications/modules/README.md)
    * [Collection](specifications/modules/readme-1/README.md)
      * [Collection Overview](specifications/modules/readme-1/collection.md)
      * [Messages](specifications/modules/readme-1/02\_messages.md)
      * [Events](specifications/modules/readme-1/03\_events.md)
      * [Future Improvements](specifications/modules/readme-1/04\_future\_improvements.md)
    * [ERC20 Overview](specifications/modules/erc20/README.md)
      * [Concepts](specifications/modules/erc20/01\_concepts.md)
      * [State](specifications/modules/erc20/02\_state.md)
      * [State Transitions](specifications/modules/erc20/03\_state\_transitions.md)
      * [Transactions](specifications/modules/erc20/04\_transactions.md)
      * [Hooks](specifications/modules/erc20/05\_hooks.md)
      * [Events](specifications/modules/erc20/06\_events.md)
      * [Parameters](specifications/modules/erc20/07\_parameters.md)
      * [Clients](specifications/modules/erc20/08\_clients.md)
* [Resources](resources/README.md)
  * [Uptick API Reference](https://pkg.go.dev/github.com/UptickNetwork/uptick)
  * [Ethermint Library API Reference](https://pkg.go.dev/github.com/tharsis/ethermint)