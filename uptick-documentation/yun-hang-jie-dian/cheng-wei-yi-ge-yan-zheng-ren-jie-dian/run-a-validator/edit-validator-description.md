# Edit Validator Description

You can edit your validator's public description. This info is to identify your validator, and will be relied on by delegators to decide which validators to stake to. Make sure to provide input for every flag below. If a flag is not included in the command the field will default to empty (`--moniker` defaults to the machine name) if the field has never been set or remain the same if it has been set in the past.

The <key_name> specifies which validator you are editing. If you choose to not include certain flags, remember that the --from flag must be included to identify the validator to update.

The `--identity` can be used as to verify identity with systems like Keybase or UPort. When using with Keybase `--identity` should be populated with a 16-digit string that is generated with a [keybase.io (opens new window)](https://keybase.io/)account. It's a cryptographically secure method of verifying your identity across multiple online networks. The Keybase API allows us to retrieve your Keybase avatar. This is how you can add a logo to your validator profile.

```sh
uptickd tx staking edit-validator
  --moniker="choose a moniker" 
  --website="https://uptick.network" 
  --identity=6A0D65E29A4CBC8E 
  --details="To infinity and beyond!" 
  --chain-id=<chain_id> 
  --gas="auto" 
  --gas-prices="0.025auptick" 
  --from=<key_name> 
  --commission-rate="0.10"
```

Note: The `commission-rate` value must adhere to the following invariants:

* Must be between 0 and the validator's `commission-max-rate`
* Must not exceed the validator's `commission-max-change-rate` which is maximum % point change rate per day. In other words, a validator can only change its commission once per day and within `commission-max-change-rate` bounds.
