# Run a Testnet Validator

Claim your testnet Uptick on the [faucet](https://docs.uptick.network/testnet/faucet.html) using your validator account address and submit your validator account address:

{% hint style="info" %}
NOTE: Until `uptickd status 2>&1 | jq ."SyncInfo"."catching_up"` got false, create your validator. If your validator is jailed, unjail it via `uptickd tx slashing unjail --from <wallet name> --chain-id uptick_7000-2 -y -b block`.
{% endhint %}

{% hint style="info" %}
For more details on how to configure your validator, follow the validator [setup](https://docs.uptick.network/guides/validators/setup.html) instructions.
{% endhint %}

```sh
uptickd tx staking create-validator \
  --amount=5000000000000000000auptick \
  --pubkey=$(uptickd tendermint show-validator) \
  --moniker=<$moniker>" \
  --chain-id=uptick_7000-2 \
  --commission-rate="0.10" \
  --commission-max-rate="0.20" \
  --commission-max-change-rate="0.01" \
  --min-self-delegation="1000000" \
  --gas="auto" \
  --from=<$wallet name> \
  -y \
  -b block
```
