# Status

Query node statusFlags:\


| Name, shorthand | Default                                         | Description                                                | Required |
| --------------- | ----------------------------------------------- | ---------------------------------------------------------- | -------- |
| --node, -n      | tcp://[localhost:26657](http://localhost:26657) | \<host>:\<port> to tendermint rpc interface for this chain |          |

Query node status

```Bash
uptickd status
```

Example Output:

```sh
{
    "NodeInfo": {
        "protocol_version": {
            "p2p": "8",
            "block": "11",
            "app": "0"
        },
        "id": "4e9c4865b96e4675da9322d50e1ec439161d56ea",
        "listen_addr": "tcp://0.0.0.0:26656",
        "network": "origin_1170-1",
        "version": "v0.34.26",
        "channels": "40202122233038606100",
        "moniker": "origin",
        "other": {
            "tx_index": "on",
            "rpc_address": "tcp://0.0.0.0:26657"
        }
    },
    "SyncInfo": {
        "latest_block_hash": "4C8D663A7D38D2AC0044FC49B3C18EDA4E85DB44FD0A2F9B30CD5140111C7AB0",
        "latest_app_hash": "097B22EBD4F6BB224393DCD5F830B0094C1FAF8F852A26BCE2BEF7156C3DF983",
        "latest_block_height": "450944",
        "latest_block_time": "2023-06-14T11:44:03.830074075Z",
        "earliest_block_hash": "11BA0B619C8E5D1CC65053C2092E95A5C072AD54101CA3CDEDBE55522191593E",
        "earliest_app_hash": "E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855",
        "earliest_block_height": "1",
        "earliest_block_time": "2023-05-19T06:00:00Z",
        "catching_up": false
    },
    "ValidatorInfo": {
        "Address": "3BF2DB3947FFBF243143F613112BB3590E79FBEE",
        "PubKey": {
            "type": "tendermint/PubKeyEd25519",
            "value": "KRdf+0pQtHrWb2gvAMyiohaxC7trdRr+fV92mke/3ZY="
        },
        "VotingPower": "300000001"
    }
}
```
