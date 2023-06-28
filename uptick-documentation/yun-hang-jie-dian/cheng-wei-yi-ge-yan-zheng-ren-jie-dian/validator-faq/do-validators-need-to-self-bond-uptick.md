# Do validators need to self-bond UPTICK

No, they do not. A validators total stake is equal to the sum of its own self-bonded stake and of its delegated stake. This means that a validator can compensate its low amount of self-bonded stake by attracting more delegators. This is why reputation is very important for validators.

Even though there is no obligation for validators to self-bond UPTICK, delegators should want their validator to have self-bonded UPTICK in their staking pool. In other words, validators should have skin-in-the-game.

In order for delegators to have some guarantee about how much skin-in-the-game their validator has, the latter can signal a minimum amount of self-bonded UPTICK. If a validator's self-bond goes below the limit that it predefined, this validator and all of its delegators will unbond.
