#   EVM Smart Contract

Since the introduction of Ethereum in 2015, the ability to control digital assets through smart contracts has attracted a large community of developers to build decentralized applications on the Ethereum Virtual Machine.

Whether you are building new use cases on Uptick or porting an existing dApp from another EVM-based chain (e.g. Ethereum), you can easily build and deploy EVM smart contracts on Uptick to implement the core business logic of your dApp. Uptick is fully compatible with the EVM, so it allows you to use the same tools (Solidity, Remix, Oracles, etc.) and APIs (i.e. Ethereum JSON-RPC) that are available on the EVM.

Leveraging the interoperability of Cosmos chains, Uptick enables you to build scalable cross-chain applications within a familiar EVM environment. Learn about the essential components when building and deploying EVM smart contracts on Uptick below.

# Build Smart Contract with Solidity

You can develop EVM smart contracts on Uptick using [Solidity](https://docs.soliditylang.org/en/latest/), which is also used on Ethereum. If you have deployed smart contracts on Ethereum or any other EVM-compatible chain, you can use the same contracts on Uptick.

Since it is the most widely used smart contract programming language in Blockchain, Solidity comes with well-documented and rich language support.

### EVM Extensions

EVM Extensions are precompiled contracts that are built into the Ethereum Virtual Machine (EVM). Each offers specific functionality, that can be used by other smart contracts. Generally, they are used to perform operations that are either not possible or would be too expensive to perform with a regular smart contract implementation, such as hashing, elliptic curve cryptography, and modular exponentiation.

By adding custom EVM extensions to Ethereum's basic feature set, Uptick allows developers to use previously unavailable functionality in smart contracts, like staking and governance operations. This will allow more complex smart contracts to be built on Uptick and further improves the interoperability between Cosmos and Ethereum. It also is a key feature to achieve Uptick vision of being the definitive dApp chain, where any dApp can be deployed once and users can interact with a wide range of different blockchains natively.

To enable the described functionalities, Uptick introduces so-called stateful precompiled smart contracts, which can perform a state transition, as opposed to those offered by the standard Go-Ethereum implementation, which can only read state information. This is necessary because an operation like e.g. staking tokens will ultimately change the chain state.

#   Deploy with Ethereum JSON-RPC

Uptick is fully compatible with the [Ethereum JSON-RPC APIs](https://ethereum.org/en/developers/docs/apis/json-rpc/), allowing you to deploy and interact with smart contracts on Uptick and connect with existing Ethereum-compatible web3 tooling. This gives you direct access to reading Ethereum-formatted transactions or sending them to the network which otherwise wouldn't be possible on a Cosmos chain, such as Uptick.