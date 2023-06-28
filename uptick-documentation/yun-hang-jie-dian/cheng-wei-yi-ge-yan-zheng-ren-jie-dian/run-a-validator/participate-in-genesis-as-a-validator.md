# Participate in Genesis as a Validator

If you want to participate in genesis as a validator, you need to justify that you have some stake at genesis, create one (or multiple) transactions to bond this stake to your validator address, and include this transaction in the genesis file.

Your `uptickvalconspub` can be used to create a new validator by staking tokens. You can find your validator pubkey by running:

```Solidity
uptickd tendermint show-validator
```

Next, craft your `uptickd gentx` command.

{% hint style="info" %}
A `gentx` is a JSON file carrying a self-delegation. All genesis transactions are collected by a `genesis coordinator` and validated against an initial `genesis.json`.
{% endhint %}

```sh
uptickd gentx \
  --amount <amount_of_delegation_auptick> \
  --commission-rate <commission_rate> \
  --commission-max-rate <commission_max_rate> \
  --commission-max-change-rate <commission_max_change_rate> \
  --pubkey <consensus_pubkey> \
  --name <key_name>
```

{% hint style="info" %}
When specifying commission parameters, the `commission-max-change-rate` is used to measure % _point_ change over the `commission-rate`. E.g. 1% to 2% is a 100% rate increase, but only 1 percentage point.
{% endhint %}

You can then submit your `gentx` on the [launch repository](https://github.com/cosmos/launch). These `gentx` will be used to form the final genesis file.
