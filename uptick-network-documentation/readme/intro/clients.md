# Clients

Learn about the client supported by your Uptick node.

## Client Servers

The Uptick client supports both [gRPC endpoints](https://cosmos.network/rpc) from the SDK and [Ethereum's JSON-RPC](https://eth.wiki/json-rpc/API).

### Cosmos gRPC and Tendermint RPC

Uptick exposes gRPC endpoints (and REST) for all the integrated Cosmos-SDK modules. This makes it easier for wallets and block explorers to interact with the proof-of-stake logic and native Cosmos transactions and queries:

### Ethereum JSON-RPC server

Uptick also supports most of the standard web3 [JSON-RPC APIs](https://github.com/starrymedia/upticknetworkdocs/blob/main/api/json-rpc/running\_server/README.md) to connect with existing web3 tooling.

{% hint style="info" %}
See the list of supported JSON-RPC API [endpoints](https://github.com/starrymedia/upticknetworkdocs/blob/main/api/json-rpc/endpoints/README.md) and [namespaces](https://github.com/starrymedia/upticknetworkdocs/blob/main/api/json-rpc/namespaces/README.md).
{% endhint %}

To connect to the JSON-PRC server, start the node with the `--json-rpc.enable=true` flag and define the namespaces that you would like to run using the `--evm.rpc.api` flag (e.g. `"txpool,eth,web3,net,personal"`. Then, you can point any Ethereum development tooling to `http://localhost:8545` or whatever port you choose with the listen address flag (`--json-rpc.address`).
