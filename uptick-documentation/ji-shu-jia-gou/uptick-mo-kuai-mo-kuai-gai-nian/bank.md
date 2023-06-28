---
description: Bank module allows you to manage assets in your local accounts.
---

# Bank

#### Available Commands

<table><thead><tr><th width="237">Name</th><th>Description</th></tr></thead><tbody><tr><td>balances</td><td>Query for account balances by address</td></tr><tr><td>total</td><td>Query the total supply of coins of the chain</td></tr><tr><td>denom-metadata</td><td>Query the client metadata for coin denominations</td></tr></tbody></table>

#### uptickd query bank balances

Query the total balance of an account or of a specific denomination.

```Bash
uptickd query bank balances [address] [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="88">Type</th><th width="92">Required</th><th width="106">Default</th><th>Description</th></tr></thead><tbody><tr><td>-h, --help</td><td></td><td></td><td></td><td>help for balances</td></tr><tr><td>--denom</td><td>string</td><td></td><td></td><td>The specific balance denomination to query for</td></tr><tr><td>--count-total</td><td></td><td></td><td></td><td>count total number of records in all balances to query for</td></tr></tbody></table>

#### uptickd query bank total

Query total supply of coins that are held by accounts in the chain.

```Bash
uptickd query bank total [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="77">Type</th><th width="101">Required</th><th width="92">Default</th><th>Description</th></tr></thead><tbody><tr><td>-h, --help</td><td></td><td></td><td></td><td>help for balances</td></tr><tr><td>--denom</td><td>string</td><td></td><td></td><td>The specific balance denomination to query for</td></tr></tbody></table>

#### uptickd tx bank send

Sending tokens to another address, this command includes `generate`, `sign` and `broadcast` steps.

```Bash
uptickd tx bank send [from_key_or_address] [to_address] [amount] [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="82">Type</th><th width="113">Required</th><th width="118">Default</th><th>Description</th></tr></thead><tbody><tr><td>-h, --help</td><td></td><td></td><td></td><td>Help for balances</td></tr></tbody></table>
