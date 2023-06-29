# Ethereum JSON-RPC

The [JSON-PRC](http://www.jsonrpc.org/specification) Server provides an API that allows you to connect to the Evmos blockchain and interact with the EVM. This gives you direct access to reading Ethereum-formatted transactions or sending them to the network which otherwise wouldn't be possible on a Cosmos chain, such as Evmos.

JSON-RPC is a stateless, light-weight remote procedure call (RPC) protocol. It defines several data structures and the rules around their processing. JSON-RPC is provided on multiple transports. Evmos supports JSON-RPC over HTTP and WebSocket. Transports must be enabled through command-line flags or through the app.toml configuration file. It uses JSON ([RFC 4627](https://www.ietf.org/rfc/rfc4627.txt)) as data format.

More on Ethereum JSON-RPC:

  * [EthWiki JSON-RPC API](https://eth.wiki/json-rpc/API)
  * [Geth JSON-RPC Server](https://geth.ethereum.org/docs/interacting-with-geth/rpc)
  * [Ethereum's PubSub JSON-RPC API](https://geth.ethereum.org/docs/interacting-with-geth/rpc/pubsub)

