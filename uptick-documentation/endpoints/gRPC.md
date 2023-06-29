# gRPC Client

Uptick (depends on Cosmos-SDK v0.41) introduced Protobuf as the main [encoding](https://github.com/cosmos/cosmos-sdk/blob/master/docs/core/encoding.md) library, and this brings a wide range of Protobuf-based tools that can be plugged into the SDK. One such tool is [gRPC](https://grpc.io/), a modern open source high performance RPC framework that has decent client support in several languages.

# gRPC Server Port, Activation and Configuration

The grpc.Server is a concrete gRPC server, which spawns and serves any gRPC requests. This server can be configured inside ~/.uptick/config/app.toml:

  * grpc.enable = true|false field defines if the gRPC server should be enabled. Defaults to true. 
  * grpc.address = {string} field defines the address (really, the port, since the host should be kept at 0.0.0.0) the server should bind to. Defaults to 0.0.0.0:9000.
  * Once the gRPC server is started, you can send requests to it using a gRPC client.

#gRPC Endpoints

An overview of all available gRPC endpoints shipped with the Uptick is [Protobuf documention](../../pubilc/protobuf/readme.md).
