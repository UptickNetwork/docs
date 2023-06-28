# Reset Chain Database

There shouldn't be any chain database yet, but in case there is for some reason, you should reset it. This is a good idea especially if you ran `uptickd start` on an old, broken genesis file.

```
uptickd tendermint unsafe-reset-all
```
