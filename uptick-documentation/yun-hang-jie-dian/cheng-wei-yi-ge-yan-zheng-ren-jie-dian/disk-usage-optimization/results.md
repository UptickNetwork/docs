# Results

Below is the disk usage after two weeks of Uptick Arsia Mons testnet. The default configuration results in disk usage of 90GB.

```sh
5.3G    ./state.db
70G     ./application.db
20K     ./snapshots/metadata.db
24K     ./snapshots
9.0G    ./blockstore.db
20K     ./evidence.db
1018M   ./cs.wal
4.7G    ./tx_index.db
90G     .
```

This optimized configuration has reduced the disk usage to 17 GB.

```sh
17G     .
1.1G    ./cs.wal
946M    ./application.db
20K     ./evidence.db
9.1G    ./blockstore.db
24K     ./snapshots
20K     ./snapshots/metadata.db
5.3G    ./state.db
```
