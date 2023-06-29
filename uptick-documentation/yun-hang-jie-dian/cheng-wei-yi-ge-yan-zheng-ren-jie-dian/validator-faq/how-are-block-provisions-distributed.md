# How are block provisions distributed?

Block provisions (rewards) are distributed proportionally to all validators relative to their total stake (voting power). This means that even though each validator gains UPTICK with each provision, all validators will still maintain equal weight.Let us take an example where we have 10 validators with equal staking power and a commission rate of 1%. Let us also assume that the provision for a block is 1000 UPTICK and that each validator has 20% of self-bonded UPTICK. These tokens do not go directly to the proposer. Instead, they are evenly spread among validators. So now each validator's pool has 100 UPTICK. These 100 UPTICK will be distributed according to each participant's stake:

* Commission: `100*80%*1% = 0.8 UPTICK`
* Validator gets: `100*20% + Commission = 20.8 UPTICK`
* All delegators get: `100*80% - Commission = 79.2 UPTICK`

Then, each delegator can claim its part of the 79.2 UPTICK in proportion to their stake in the validator's staking pool. Note that the validator's commission is not applied on block provisions. Note that block rewards (paid in UPTICK) are distributed according to the same mechanism.
