# Unjail Validator

When a validator is "jailed" for downtime, you must submit an `Unjail` transaction from the operator account in order to be able to get block proposer rewards again (depends on the zone fee distribution).

```Solidity
uptickd tx slashing unjail 
  --from=<key_name> 
  --chain-id=<chain_id>
```
