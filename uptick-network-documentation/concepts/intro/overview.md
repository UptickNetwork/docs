# High-level Overview

Learn about Uptick and its primary features.

## What is Uptick

Uptick is a scalable, high-throughput Proof-of-Stake blockchain that is fully compatible and interoperable with Ethereum. It's built using the [Cosmos SDK](https://github.com/cosmos/cosmos-sdk/) which runs on top of [Tendermint Core](https://github.com/tendermint/tendermint) consensus engine.

Uptick allows for running vanilla Ethereum as a [Cosmos](https://cosmos.network/) application-specific blockchain. This allows developers to have all the desired features of Ethereum, while at the same time, benefit from Tendermint’s PoS implementation. Also, because it is built on top of the Cosmos SDK, it will be able to exchange value with the rest of the Cosmos Ecosystem through the Inter Blockchain Communication Protocol (IBC).

### Features

Here’s a glance at some of the key features of Uptick:

* Web3 and EVM compatibility
* High throughput via [Tendermint Core](https://github.com/tendermint/tendermint)
* Horizontal scalability via [IBC](https://cosmos.network/ibc)
* Fast transaction finality

Uptick enables these key features by:

* Implementing Tendermint Core's Application Blockchain Interface ([ABCI](https://docs.tendermint.com/master/spec/abci/)) to manage the blockchain
* Leveraging [modules](https://docs.cosmos.network/main/building-modules/intro.html) and other mechanisms implemented by the [Cosmos SDK](https://docs.cosmos.network/).
* Utilizing [`geth`](https://github.com/ethereum/go-ethereum) as a library to promote code reuse and improve maintainability.
* Exposing a fully compatible Web3 [JSON-RPC](../../api/json-rpc/server.md) layer for interacting with existing Ethereum clients and tooling ([Metamask](../../guides/keys-wallets/metamask.md), [Remix](../../guides/tools/remix.md), [Truffle](../../guides/tools/truffle.md), etc).

The sum of these features allows developers to leverage existing Ethereum ecosystem tooling and software to seamlessly deploy smart contracts which interact with the rest of the Cosmos [ecosystem](https://cosmos.network/ecosystem)!

## Quick Facts Table

| Property              | Value       |
| --------------------- | ----------- |
| Uptick Origin Testnet | `1170`      |
| Uptick Mainnet        | `117`       |
| Block Time            | ~6 seconds |
