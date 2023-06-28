# What are the slashing conditions?

If a validator misbehaves, its bonded stake along with its delegators' stake and will be slashed. The severity of the punishment depends on the type of fault. There are 3 main faults that can result in slashing of funds for a validator and its delegators:

* **Double-signing:** If someone reports on chain A that a validator signed two blocks at the same height on chain A and chain B, and if chain A and chain B share a common ancestor, then this validator will get slashed on chain A.
* **Downtime:** If a validator misses more than 95% of the last 10.000 blocks, they will get slashed by 0.01%.
* **Unavailability:** If a validator's signature has not been included in the last X blocks, the validator will get slashed by a marginal amount proportional to X. If X is above a certain limit Y, then the validator will get unbonded.
* **Non-voting:** If a validator did not vote on a proposal, its stake could receive a minor slash.

Note that even if a validator does not intentionally misbehave, it can still be slashed if its node crashes, looses connectivity, gets DDoSed, or if its private key is compromised.
