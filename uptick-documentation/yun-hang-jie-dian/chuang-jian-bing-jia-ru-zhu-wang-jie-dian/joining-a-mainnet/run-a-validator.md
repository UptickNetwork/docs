# Run a Validator

Confirm your node has caught-up

```sh
# if you have not installed jq
# apt-get update && apt-get install -y jq

# if the output is false, means your node has caught-up
uptickd status | jq .sync_info.catching_up
```

{% hint style="info" %}
For more details on how to configure your validator, follow the validator [setup](https://docs.uptick.network/guides/validators/setup.html) instructions.
{% endhint %}

```sh
uptickd tx staking create-validator \
  --amount=5000000000000000000auptick \
  --chain-id=uptick_117-1 \
  --commission-rate="0.10" \
  --commission-max-rate="0.20" \
  --commission-max-change-rate="0.01" \
  --min-self-delegation="1000000" \
  --moniker="moniker" \
  --identity="identity" \
  --website="website" \
  --details="details" \
  --from=<$Validator wallet name> \
  -y -b block
```
