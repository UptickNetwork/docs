# Create Your Validator

Your `uptickvalconspub` can be used to create a new validator by staking tokens. You can find your validator pubkey by running:

```Solidity
uptickd tendermint show-validator
```

To create your validator, just use the following command:

```sh
uptickd tx staking create-validator \
  --amount=1000000auptick \
  --pubkey=$(uptickd tendermint show-validator) \
  --moniker="choose a moniker" \
  --chain-id=<chain_id> \
  --commission-rate="0.10" \
  --commission-max-rate="0.20" \
  --commission-max-change-rate="0.01" \
  --min-self-delegation="1000000" \
  --gas="auto" \
  --gas-prices="0.025auptick" \
  --from=<key_name>
```

{% hint style="info" %}
When specifying commission parameters, the `commission-max-change-rate` is used to measure % _point_ change over the `commission-rate`. E.g. 1% to 2% is a 100% rate increase, but only 1 percentage point.
{% endhint %}

{% hint style="info" %}
`Min-self-delegation` is a strictly positive integer that represents the minimum amount of self-delegated voting power your validator must always have. A `min-self-delegation` of `1000000` means your validator will never have a self-delegation lower than `1 auptick`
{% endhint %}

You can confirm that you are in the validator set by using a third party explorer.
