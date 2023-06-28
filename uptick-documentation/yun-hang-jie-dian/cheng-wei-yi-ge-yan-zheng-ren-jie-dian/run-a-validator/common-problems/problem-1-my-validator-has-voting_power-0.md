# Problem #1: My validator has voting\_power: 0

Your validator has become jailed. Validators get jailed, i.e. get removed from the active validator set, if they do not vote on `500` of the last `10000` blocks, or if they double sign.If you got jailed for downtime, you can get your voting power back to your validator. First, if `uptickd` is not running, start it up again:

```Solidity
uptickd start
```

Wait for your full node to catch up to the latest block. Then, you can [unjail your validator](https://docs.uptick.network/guides/validators/setup.html#unjail-validator)Lastly, check your validator again to see if your voting power is back.

```Solidity
uptickd status
```

You may notice that your voting power is less than it used to be. That's because you got slashed for downtime!
