# Configure pruning

By default every 500th state, and the last 100 states are kept. This consumes a lot of disk space on long run, and can be optimized with following custom configuration:

```sh
pruning = "custom"
pruning-keep-recent = "100"
pruning-keep-every = "0"
pruning-interval = "10"
```

\
Configuring `pruning-keep-recent = "0"` might sound tempting, but this will risk database corruption if the `uptickd` is killed for any reason. Thus, it is recommended to keep the few latest states.
