# What is "staking"?

Uptick is a public Proof-of-Stake (PoS) blockchain, meaning that validator's weight is determined by the amount of staking tokens (UPTICK) bonded as collateral. These staking tokens can be staked directly by the validator or delegated to them by UPTICK holders.Any user in the system can declare its intention to become a validator by sending a [`create-validator`](https://docs.uptick.network/guides/validators/faq.html#how-to-become-a-validator) transaction. From there, they become validators.The weight (i.e. total stake or voting power) of a validator determines wether or not it is an active validator, and also how frequently this node will have to propose a block and how much revenue it will obtain. Initially, only the top 150 validators with the most weight will be active validators. If validators double-sign, or are frequently offline, they risk their staked tokens (including UPTICK delegated by users) being "slashed" by the protocol to penalize negligence and misbehavior.