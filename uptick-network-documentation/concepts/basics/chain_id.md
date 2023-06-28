# Chain ID

Learn about the Uptick chain-id format

## Official Chain IDs

Testnets

| Name                  | Chain ID        | Identifier | EIP155 Number | Version Number |
| --------------------- | --------------- | ---------- | ------------- | -------------- |
| Uptick Origin Testnet | `origin_1170-1` | `uptick`   | `1170`        | `1`            |

Mainnet

| Name   | Chain ID       | Identifier | EIP155 Number | Version Number                               |
| ------ | -------------- | ---------- | ------------- | -------------------------------------------- |
| Uptick | `uptick_117-1` | `uptick`   | `117`         |  `1` |

{% hint style="info" %}
You can also lookup the [EIP155](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md) `Chain ID` by referring to [chainlist.org](https://chainlist.org/).
{% endhint %}

## The Chain Identifier

Every chain must have a unique identifier or `chain-id`. Tendermint requires each application to define its own `chain-id` in the [genesis.json fields](https://docs.tendermint.com/master/spec/core/genesis.html#genesis-fields). However, in order to comply with both EIP155 and Cosmos standard for chain upgrades, Uptick-compatible chains must implement a special structure for their chain identifiers.

## Structure

The Uptick Chain ID contains 3 main components

* **Identifier**: Unstructured string that defines the name of the application.
* **EIP155 Number**: Immutable [EIP155](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md) `CHAIN_ID` that defines the replay attack protection number.
* **Version Number**: Is the version number (always positive) that the chain is currently running. This number **MUST** be incremented every time the chain is upgraded or forked in order to avoid network or consensus errors.

### Format

The format for specifying and Uptick compatible chain-id in genesis is the following:

```bash
{identifier}_{EIP155}-{version}
```

The following table provides an example where the second row corresponds to an upgrade from the first one:

:::: tabs
::: tab Testnets

| ChainID         | Identifier | EIP155 Number | Version Number |
| --------------- | ---------- | ------------- | -------------- |
| `origin_1170-1` | origin     | 1170          | 1              |

:::
::: tab Mainnet

| ChainID        | Identifier | EIP155 Number | Version Number |
| -------------- | ---------- | ------------- | -------------- |
| `uptick_117-1` | uptick     | 117           | 1              |

:::
::::