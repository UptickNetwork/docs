---
description: Tx module allows you to sign or broadcast transactions
---

# Tx

#### Available Commands

<table><thead><tr><th width="242">Name</th><th>Description</th></tr></thead><tbody><tr><td>sign</td><td>Sign transactions generated offline</td></tr><tr><td>broadcast</td><td>Broadcast a signed transaction to the network</td></tr><tr><td>multi-sign</td><td>Generate multisig signatures for transactions generated offline</td></tr><tr><td>tx</td><td>Query for a transaction by hash in a committed block</td></tr><tr><td>txs</td><td>Search for transactions that match the exact given events where results are paginated</td></tr></tbody></table>

#### uptickd tx sign

Sign transactions in generated offline file. The file created with the --generate-only flag.

```Bash
uptickd tx sign [file] [flags]
```

Flags

| Name, shorthand  | Type   | Required | Default | Description                                                                        |
| ---------------- | ------ | -------- | ------- | ---------------------------------------------------------------------------------- |
| --append         | bool   | TRUE     | TRUE    | Attach a signature to an existing signature.                                       |
| --from           | string | TRUE     |         | Key name for signature                                                             |
| --offline        | bool   | TRUE     |         | Offline mode.                                                                      |
| --signature-only | bool   | TRUE     |         | Print only the generated signature, then exit                                      |
| --multisig       | string |          | TRUE    | Address of the multisig account on behalf of which the transaction shall be signed |

Generate an offline tx

> **TIP**
>
> You can generate any type of txs offline by appending the flag `--generate-only`

We use a transfer tx in the following examples:

```Bash
uptickd tx bank send [from_key_or_address] [to_address] [amount] [flags]
```

Sign tx offline

```Bash
uptickd tx sign unsigned.json --name=<key-name> > signed.tx
```

#### uptickd tx broadcast

This command is used to broadcast an offline signed transaction to the network.Broadcast offline signed transaction

```Bash
uptickd tx broadcast signed.json --chain-id=...
```

#### uptickd tx multisign

Sign a transaction by multiple accounts. The tx could be broadcasted only when the number of signatures meets the multisig-threshold.

```Bash
uptickd tx multisign <file> <key-name> <[signature]...> [flags]
```

Sign the multisig txQuery the multisig address

```Bash
uptickd keys show <multisig-keyname>
```

Sign the `unsigned.json`Assume the multisig-threshold is 2, here we sign the `unsigned.json` by 2 of the signersSign the tx by signer-1:

<pre class="language-Bash"><code class="lang-Bash"><strong>uptickd tx sign unsigned.json --from=&#x3C;signer-keyname-1> --chain-id=&#x3C;chain-id> --multisig=&#x3C;multisig-address> --signature-only > signed-1.json
</strong></code></pre>

Sign the tx by signer-2:

<pre class="language-Bash"><code class="lang-Bash"><strong>uptickd tx sign unsigned.json --from=&#x3C;signer-keyname-2> --chain-id=&#x3C;chain-id> --multisig=&#x3C;multisig-address> --signature-only > signed-2.json
</strong></code></pre>

Merge the signaturesMerge all the signatures into `signed.json`

```Bash
uptickd tx multisign --chain-id=<chain-id> unsigned.json <multisig-keyname> signed-1.json signed-2.json > signed.json
```

Now you can broadcast the signed tx.

#### uptickd query tx

```Bash
uptickd query tx [hash] [flags]

```

#### uptickd query txs

```Bash
iris query txs --events 'message.sender=<uptick...>&message.action=xxxx' --page 1 --limit 30

```
