# How are fees distributed?

Fees are similarly distributed with the exception that the block proposer can get a bonus on the fees of the block it proposes if it includes more than the strict minimum of required precommits.

When a validator is selected to propose the next block, it must include at least ⅔ precommits for the previous block in the form of validator signatures. However, there is an incentive to include more than ⅔ precommits in the form of a bonus. The bonus is linear: it ranges from 1% if the proposer includes ⅔rd precommits (minimum for the block to be valid) to 5% if the proposer includes 100% precommits. Of course the proposer should not wait too long or other validators may timeout and move on to the next proposer. As such, validators have to find a balance between wait-time to get the most signatures and risk of losing out on proposing the next block. This mechanism aims to incentivize non-empty block proposals, better networking between validators as well as to mitigate censorship.

Let's take a concrete example to illustrate the aforementioned concept. In this example, there are 10 validators with equal stake. Each of them applies a 1% commission and has 20% of self-bonded UPTICK. Now comes a successful block that collects a total of 1005 UPTICK in fees. Let's assume that the proposer included 100% of the signatures in its block. It thus obtains the full bonus of 5%.

We have to solve this simple equation to find the reward  _`R`_R for each validator:

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>





