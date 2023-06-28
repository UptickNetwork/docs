# Indexing

If you do not need to query transactions from the specific node, you can disable indexing. On `config.toml` set

```sh
indexer = "null"
```

If you do this on already synced node, the collected index is not purged automatically, you need to delete it manually. The index is located under the database directory with name `data/tx_index.db/`.
