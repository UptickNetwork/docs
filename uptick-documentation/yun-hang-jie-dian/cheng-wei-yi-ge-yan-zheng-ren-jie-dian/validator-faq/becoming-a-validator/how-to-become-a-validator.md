# How to become a validator?

Any participant in the network can signal their intent to become a validator by creating a validator and registering its validator profile. To do so, the candidate broadcasts a `create-validator` transaction, in which they must submit the following information:

* Validator's PubKey: Validator operators can have different accounts for validating and holding liquid funds. The PubKey submitted must be associated with the private key with which the validator intends to sign _prevotes_ and _precommits_.
* Validator's Address: `uptickvaloper1-` address. This is the address used to identify your validator publicly. The private key associated with this address is used to bond, unbond, and claim rewards.
* Validator's name (also known as the moniker)
* Validator's website _(optional)_
* Validator's description _(optional)_
* Initial commission rate: The commission rate on block provisions, block rewards and fees charged to delegators.
* Maximum commission: The maximum commission rate which this validator will be allowed to charge.
* Commission change rate: The maximum daily increase of the validator commission.
* Minimum self-bond amount: Minimum amount of UPTICK the validator needs to have bonded at all times. If the validator's self-bonded stake falls below this limit, its entire staking pool will be unbonded.
* Initial self-bond amount: Initial amount of UPTICK the validator wants to self-bond.

```sh
 uptickd tx staking create-validator
    --pubkey uptickvalconspub1zcjduepqs5s0vddx5m65h5ntjzwd0x8g3245rgrytpds4ds7vdtlwx06mcesmnkzly
    --amount "2auptick"
    --from tmp
    --commission-rate="0.20"
    --commission-max-rate="1.00"
    --commission-max-change-rate="0.01"
    --min-self-delegation "1"
    --moniker "validator"
    --chain-id "uptick_7000-2"
    --gas auto
    --node tcp://127.0.0.1:26647
```

Once a validator is created and registered, UPTICK holders can delegate UPTICK to it, effectively adding stake to its pool. The total stake of a validator is the sum of the UPTICK self-bonded by the validator's operator and the UPTICK bonded by external delegators.Only the top 150 validators with the most stake are considered the active validators, becoming bonded validators. If ever a validator's total stake dips below the top 150, the validator loses its validator privileges (meaning that it won't generate rewards) and no longer serves as part of the active set (i.e doesn't participate in consensus), entering unbonding mode and eventually becomes unbonded.
