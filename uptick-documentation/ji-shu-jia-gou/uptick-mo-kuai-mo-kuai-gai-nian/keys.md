---
description: Keys allows you to manage your local tendermint keystore (wallets) for iris.
---

# Keys

#### Available Commands

<table><thead><tr><th width="269">Name</th><th>Description</th></tr></thead><tbody><tr><td>add</td><td>Add an encrypted private key (either newly generated or recovered), encrypt it, and save to &#x3C;name> file</td></tr><tr><td>delete</td><td>Delete the given keys</td></tr><tr><td>export</td><td>Export private keys</td></tr><tr><td>import</td><td>Import private keys into the local keybase</td></tr><tr><td>list</td><td>List all keys</td></tr><tr><td>migrate</td><td>Migrate keys from amino to proto serialization format</td></tr><tr><td>mnemonic</td><td>Compute the bip39 mnemonic for some input entropy</td></tr><tr><td>parse</td><td>Parse address from hex to bech32 and vice versa</td></tr><tr><td>show</td><td>Retrieve key information by name or address</td></tr><tr><td>rename</td><td>Rename an existing key</td></tr><tr><td>unsafe-export-eth-key</td><td>**UNSAFE** Export an Ethereum private key</td></tr><tr><td>unsafe-import-eth-key</td><td>**UNSAFE** Import Ethereum private keys into the local keybase</td></tr></tbody></table>

#### uptickd keys add

Derive a new private key and encrypt to disk.

```Bash
uptickd keys add <name> [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="108">Type</th><th width="86">Default</th><th width="120">Required</th><th>Description</th></tr></thead><tbody><tr><td>--multisig</td><td>strings</td><td></td><td></td><td>List of key names stored in keyring to construct a public legacy multisig key</td></tr><tr><td>--multisig-threshold</td><td>string</td><td>1</td><td></td><td>K out of N required signatures. For use in conjunction with --multisig (default 1)</td></tr><tr><td>--nosort</td><td></td><td></td><td></td><td>Keys passed to --multisig are taken in the order they're supplied</td></tr><tr><td>--pubkey</td><td>string</td><td></td><td></td><td>Parse a public key in JSON format and saves key info to &#x3C;name> file.</td></tr><tr><td>--interactive</td><td></td><td></td><td></td><td>Interactively prompt user for BIP39 passphrase and mnemonic</td></tr><tr><td>--ledger</td><td></td><td></td><td></td><td>Store a local reference to a private key on a Ledger device</td></tr><tr><td>--recover</td><td></td><td></td><td></td><td>Provide seed phrase to recover existing key instead of creating</td></tr><tr><td>--no-backup</td><td></td><td></td><td></td><td>Don't print out seed phrase (if others are watching the terminal)</td></tr><tr><td>--dry-run</td><td></td><td></td><td></td><td>Perform action, but don't add key to local keystore</td></tr><tr><td>--hd-path</td><td>string</td><td></td><td></td><td>Manual HD Path derivation (overrides BIP44 config)</td></tr><tr><td>--coin-type</td><td>uint32</td><td>60</td><td></td><td>coin type number for HD derivation (default 60)</td></tr><tr><td>--account</td><td>uint32</td><td></td><td></td><td>Account number for HD derivation (less than equal 2147483647)</td></tr><tr><td>--index</td><td>uint32</td><td></td><td></td><td>Address index number for HD derivation (less than equal 2147483647)</td></tr><tr><td>--algo</td><td>string</td><td>eth_secp256k1</td><td></td><td>Key signing algorithm to generate keys for (default "eth_secp256k1")</td></tr></tbody></table>

Create a new key

```Bash
uptickd keys add MyKey
```

{% hint style="info" %}
**WARNING**

Importantwrite the seed phrase in a safe place! It is the only way to recover your account if you ever forget your password.
{% endhint %}

Recover an existing key from seed phrase

If you forget your password or lose your key, or you wanna use your key in another place, you can recover your key by your seed phrase.

```Bash
uptickd keys add MyKey --recover
```

You'll be asked to enter the seed phrase. Then you get your key back.

```Python
> Enter your bip39 mnemonic
```

Create a multisig key

The following example creates a multisig key with 3 sub-keys, and specify the minimum number of signatures as 2. The tx could be broadcast only when the number of signatures is greater than or equal to 2.

<pre class="language-Bash"><code class="lang-Bash"><strong>uptickd keys add &#x3C;multisig-keyname> --multisig-threshold=2 --multisig=&#x3C;signer-keyname-1>,&#x3C;signer-keyname-2>,&#x3C;signer-keyname-3>
</strong></code></pre>

> **TIP**
>
> `<signer-keyname>` can be the type of "local/offline/ledger", but not "multi" type.If you don't have all the permission of sub-keys, you can ask for the pubkeys to create the offline keys first, then you will be able to create the multisig key.Offline key can be created by "uptickd keys add --pubkey".

How to use multisig key to sign and broadcast a transaction, please refer to multisign

#### uptickd keys delete

Delete a local key by the given name.

```Bash
uptickd keys delete <name>... [flags]
```

Flags:

<table><thead><tr><th width="178">Name, shorthand</th><th width="130">Default</th><th width="237">Description</th><th>Required</th></tr></thead><tbody><tr><td>--force, -f</td><td>FALSE</td><td>Remove the key unconditionally without asking for the passphrase. Deprecated</td><td></td></tr><tr><td>--yes, -y</td><td>FALSE</td><td>Skip confirmation prompt when deleting offline or ledger key references</td><td></td></tr><tr><td>--help, -h</td><td>FALSE</td><td>help for delete</td><td></td></tr></tbody></table>

Delete a local key

```Bash
uptickd keys delete MyKey
```

#### uptickd keys export

Export the keystore of a key to a json file

```Bash
uptickd keys export <name> [flags]
```

Export keystore

```Bash
uptickd keys export Mykey --output-file=<path-to-keystore>
```

#### uptickd keys import

Import a ASCII armored private key into the local keybase.

Import a ASCII armored private key

```Bash
uptickd keys import <name> <keyfile> [flags]
```

#### uptickd keys list

List all the keys stored by this key manager along with their associated name, type, address and pubkey.Flags:

<table><thead><tr><th>Name, shorthand</th><th width="107">Default</th><th>Description</th><th>Required</th></tr></thead><tbody><tr><td>--list-name</td><td></td><td>List names only</td><td></td></tr></tbody></table>

List all keys

```Bash
uptickd keys list
```

#### uptickd keys migrate

Migrate key information from the legacy (db-based) Keybase to the new keyring-based Keybase.

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="125">Default</th><th>Description</th><th>Required</th></tr></thead><tbody><tr><td>--dry-run</td><td></td><td>Run migration without actually persisting any changes to the new Keybase</td><td></td></tr></tbody></table>

Migrate key information

```Bash
uptickd keys migrate [flags]

```

#### uptickd keys mnemonic

Create a bip39 mnemonic, sometimes called a seed phrase, by reading from the system entropy. To pass your own entropy, use `unsafe-entropy` mode.

```Bash
uptickd keys mnemonic [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="103">Default</th><th>Description</th><th>Required</th></tr></thead><tbody><tr><td>--unsafe-entropy</td><td></td><td>Prompt the user to supply their own entropy, instead of relying on the system</td><td></td></tr></tbody></table>

Create a bip39 mnemonic

```Bash
uptickd keys mnemonic
```

You'll get a bip39 mnemonic with 24 words, e.g.:

```Bash
garment depart real arrow web impose place roast empty execute client lobster protect want identify upper trouble program seek ranch crumble distance gather twelve
```

#### uptickd keys parse

Convert and print to stdout key addresses and fingerprints from hexadecimal into bech32 cosmos prefixed format and vice versa.

\
Convert and print to stdout key addresses and fingerprints

```Bash
uptickd keys parse <hex-or-bech32-address> [flags]
```

#### uptickd keys show

Get details of a local key.

```Bash
uptickd keys show [name_or_address] [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="149">Default</th><th>Description</th><th>Required</th></tr></thead><tbody><tr><td>--address</td><td>FALSE</td><td>Output the address only (overrides --output)</td><td></td></tr><tr><td>--bech</td><td>acc</td><td>The Bech32 prefix encoding for a key (acc/val/cons)</td><td></td></tr><tr><td>--device</td><td>FALSE</td><td>Output the address in a ledger device</td><td></td></tr><tr><td>--multisig-threshold</td><td>1</td><td>K out of N required signatures</td><td></td></tr><tr><td>--pubkey</td><td>FALSE</td><td>Output the public key only (overrides --output)</td><td></td></tr></tbody></table>

Get details of a local key

```Bash
uptickd keys show MyKey
```

The following infos will be shown:

```Bash
- address: uptick1pw0lu7sk2tjadp68aas4xhjp4uh67e26caqv7v
  name: MyKey
  pubkey: '{"@type":"/ethermint.crypto.v1.ethsecp256k1.PubKey","key":"A0NpxhHn0V4VfdBI2VxLQiH5zsUvu48umNKUtpALyia3"}'
  type: local
```

\
Get validator operator address

If an address has been bonded to be a validator operator (which the address you used to create a validator), then you can use `--bech val` to get the operator's address prefixed by `iva` and the pubkey prefixed by `ivp`:

```Bash
uptickd keys show MyKey --bech val
```

Example Output:

```Bash
- address: uptickvaloper1pw0lu7sk2tjadp68aas4xhjp4uh67e26t94cjq
  name: MyKey
  pubkey: '{"@type":"/ethermint.crypto.v1.ethsecp256k1.PubKey","key":"A0NpxhHn0V4VfdBI2VxLQiH5zsUvu48umNKUtpALyia3"}'
  type: local
```
