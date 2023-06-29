# Params

Params module allows you to query the system parameters which can be governed (except the gov params) by the gov module.

```Bash
uptickd query params subspace [subspace] [key] [flags]
```

Subspace currently supports the following:`auth`, `bank`, `staking`, `mint`, `distribution`, `slashing`, `gov`, `crisis`, `token`, `record`, `htlc`, `coinswap`, `service`.Among them, the parameters available for query for each subspace are as follows:

#### auth

| key                    | description                                                     | default |
| ---------------------- | --------------------------------------------------------------- | ------- |
| MaxMemoCharacters      | Maximum number of characters in the memo field in a transaction | 256     |
| TxSigLimit             | Maximum number of signatures per transaction                    | 7       |
| TxSizeCostPerByte      | The amount of gas consumed per byte of the transaction          | 10      |
| SigVerifyCostED25519   | Gas spent on edd2519 algorithm signature verification           | 590     |
| SigVerifyCostSecp256k1 | Gas spent on secp256k1 algorithm signature verification         | 1000    |

#### bank

| key                | description                                        | default |
| ------------------ | -------------------------------------------------- | ------- |
| SendEnabled        | Tokens that support transfer                       | []     |
| DefaultSendEnabled | Whether to enable the transfer function by default | TRUE    |

#### staking

| key               | description                                                     | default   |
| ----------------- | --------------------------------------------------------------- | --------- |
| UnbondingTime     | Mortgage redemption time                                        | 3w(weeks) |
| MaxValidators     | Maximum number of validators                                    | 100       |
| MaxEntries        | The maximum number of unbinding/redelegation orders in progress | 7         |
| BondDenom         | Bond denom                                                      | uptick    |
| HistoricalEntries | The number of historical entries                                | 100       |

#### mint

| key       | description                 | default |
| --------- | --------------------------- | ------- |
| Inflation | Token issuance frequency    | 0.04    |
| MintDenom | Denom of the token mintable | uptick  |

#### distribution

| key                 | description                                       | default |
| ------------------- | ------------------------------------------------- | ------- |
| communitytax        | Fees charged for withdrawal                       | 0.02    |
| baseproposerreward  | The base reward rate of the block proposer        | 0.01    |
| bonusproposerreward | Reward rate for block proposers                   | 0.04    |
| withdrawaddrenabled | Whether to support setting the withdrawal address | TRUE    |

#### slashing

| key                     | description                           | default |
| ----------------------- | ------------------------------------- | ------- |
| SignedBlocksWindow      | Sliding window for downtime slashing  | 100     |
| MinSignedPerWindow      | Minimum signature rate in each window | 0.5     |
| DowntimeJailDuration    | Maximum downtime (continuous)         | 10m     |
| SlashFractionDoubleSign | Penalty coefficient for double sign   | 1/20    |
| SlashFractionDowntime   | Penalty coefficient for downtime      | 1/100   |

#### gov

| key           | description                                      | default                                                     |
| ------------- | ------------------------------------------------ | ----------------------------------------------------------- |
| depositparams | Related parameters of the deposit mortgage phase | min_deposit: 10000000uiris; max_deposit_period: 2d(days) |
| votingparams  | Related parameters of the voting mortgage phase  | voting_period: 2d(days)                                    |
| tallyparams   | Related parameters of the voting tally phase     | quorum: 0.334; threshold: 0.5; veto_threshold: 0.334       |
