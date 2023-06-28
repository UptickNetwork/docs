# Confirm Your Validator is Running

Your validator is active if the following command returns anything:

```Solidity
uptickd query tendermint-validator-set | grep "$(uptickd tendermint show-address)"
```

You should now see your validator in one of Uptick explorers. You are looking for the `bech32` encoded `address` in the `~/.uptickd/config/priv_validator.json` file.

{% hint style="info" %}
**Note**

To be in the validator set, you need to have more total voting power than the 100th validator.
{% endhint %}
