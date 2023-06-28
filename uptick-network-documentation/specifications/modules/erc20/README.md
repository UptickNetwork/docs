# ERC20 Overview

## Abstract

This document specifies the internal `x/erc20` module of the Uptick Hub.

The `x/erc20` module enables the Uptick Hub to support a trustless, on-chain bidirectional internal relaying (aka intrarelaying) of tokens between Uptick' EVM and Cosmos runtimes, specifically the `x/evm` and `x/bank` modules. This allows token holders on Uptick to instantaneously convert their native Cosmos `sdk.Coins` (in this document referred to as "Coin(s)") to ERC-20 (aka "Token(s)") and vice versa, while retaining fungibility with the original asset on the issuing environment/runtime (EVM or Cosmos) and preserving ownership of the ERC-20 contract.

This intrarelaying functionality is fully governed by native $UPTICK token holders who manage the canonical `TokenPair` registrations (ie, ERC20 ←→ Coin mappings). This governance functionality is implemented using the Cosmos-SDK `gov` module with custom proposal types for registering and updating the canonical mappings respectively.

Why is this important? Cosmos and the EVM are two runtimes that are not compatible by default. The native Cosmos Coins cannot be used in applications that require the ERC-20 standard. Cosmos coins are held on the `x/bank` module (with access to module methods like querying the supply or balances) and ERC-20 Tokens live on smart contracts. This problem is similar to [wETH](https://weth.io/), with the difference, that it not only applies to gas tokens (like $UPTICK), but to all Cosmos Coins (IBC vouchers, staking and gov coins, etc.) as well.

With the `x/erc20` users on Uptick can

* use existing native cosmos assets (like $OSMO or $ATOM) on EVM-based chains, e.g. for Trading IBC tokens on DeFi protocols, buying NFT, etc.
* transfer existing tokens on Ethereum and other EVM-based chains to Uptick to take advantage of application-specific chains in the Cosmos ecosystem
* build new applications that are based on ERC-20 smart contracts and have access to the Cosmos ecosystem.

## Contents

1. [**Concepts**](01\_concepts.md)
2. [**State**](02\_state.md)
3. [**State Transitions**](03\_state\_transitions.md)
4. [**Transactions**](04\_transactions.md)
5. [**Hooks**](05\_hooks.md)
6. [**Events**](06\_events.md)
7. [**Parameters**](07\_parameters.md)
8. [**Clients**](08\_clients.md)
