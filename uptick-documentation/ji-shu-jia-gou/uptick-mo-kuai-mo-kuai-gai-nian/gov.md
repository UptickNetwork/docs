---
description: This module provides the basic functionalities for Governance.
---

# Gov

#### Available Commands

<table><thead><tr><th width="226">Name</th><th>Description</th></tr></thead><tbody><tr><td>proposal</td><td>Query details of a single proposal</td></tr><tr><td>proposals</td><td>Query proposals with optional filter</td></tr><tr><td>vote</td><td>Query details of a single vote</td></tr><tr><td>votes</td><td>Query votes on a proposal</td></tr><tr><td>deposit</td><td>Query details of a deposit</td></tr><tr><td>deposits</td><td>Query deposits on a proposal</td></tr><tr><td>tally</td><td>Get the tally of a proposal vote</td></tr><tr><td>param</td><td>Query the parameters (voting</td></tr><tr><td>params</td><td>Query the parameters of the governance process</td></tr><tr><td>proposer</td><td>Query which address proposed a proposal with a given ID.</td></tr><tr><td>draft-proposal</td><td>Draft any type of proposal</td></tr><tr><td>submit-proposal</td><td>Submit a proposal along with an initial deposit</td></tr><tr><td>submit-legacy-proposal</td><td>Submit a legacy proposal along with an initial deposit</td></tr><tr><td>deposit</td><td>Deposit tokens for an active proposal</td></tr><tr><td>vote</td><td>Vote for an active proposal, options: yes/no/no_with_veto/abstain</td></tr><tr><td>weighted-vote</td><td>Submit a weighted vote for a given governance proposal</td></tr></tbody></table>

#### uptickd query gov proposal

Query details of a proposal.

```Bash
uptickd query gov proposal [proposal-id] [flags]
```

Query a proposal

```Bash
uptickd query gov proposal <proposal-id>
```

#### uptickd query gov proposals

Query proposals with optional filter.

```Bash
uptickd query gov proposals [flags]
```

<table><thead><tr><th>Name, shorthand</th><th width="103">Type</th><th width="118">Required</th><th width="116">Default</th><th>Description</th></tr></thead><tbody><tr><td>--depositor</td><td>string</td><td></td><td></td><td>(optional) filter by proposals deposited on by depositor</td></tr><tr><td>--limit</td><td>uint</td><td></td><td></td><td>pagination limit of proposals to query for (default 100)</td></tr><tr><td>--status</td><td>string</td><td></td><td></td><td>(optional) filter proposals by proposal status, status: deposit_period/voting_period/passed/rejected</td></tr><tr><td>--voter</td><td>string</td><td></td><td></td><td>(optional) filter by proposals voted on by voted</td></tr></tbody></table>

Query all proposals

```Bash
uptickd query gov proposals
```

Query proposals by conditions

```Bash
uptickd query gov proposals --limit=3 --status=Passed --depositor=<uptick...>
```

#### uptickd query gov vote

Query details of a single vote.

```Bash
uptickd query gov vote [proposal-id] [voter-addr] [flags]
```

Query a vote

```Bash
uptickd query gov vote [proposal-id] [voter-addr] [flags]
```

#### uptickd query gov votes

Query votes on a proposal.

```Bash
uptickd query gov votes [proposal-id] [flags]
```

Query all votes of a proposal

```Bash
uptickd query gov votes <proposal-id>
```

#### uptickd query gov deposits

Query details for all deposits on a proposal.

```Bash
uptickd query gov deposits [proposal-id] [flags]
```

Query all deposits of a proposal

```Bash
uptickd query gov deposits <proposal-id>
```

#### uptickd query gov tally

Query tally of votes on a proposal. You can find the proposal-id by running "uptickd query gov proposals".

```Bash
uptickd query gov tally [proposal-id] [flags]
```

Query the statistics of a proposal

```Bash
uptickd query gov tally <proposal-id>
```

#### uptickd query gov param

Query the parameters (voting|tallying|deposit) of the governance process.

```Bash
uptickd query gov param [param-type] [flags]
```

Example:

> ```Bash
> uptickd query gov param voting
> > uptickd query gov param tallying
> > uptickd query gov param deposit
> ```

#### uptickd query gov params

Query the all the parameters for the governance process.

```Bash
uptickd query gov params [flags]
```

#### uptickd query gov proposer

Query which address proposed a proposal with a given ID.

```Bash
uptickd query gov proposer [proposal-id] [flags]
```

#### uptickd tx gov draft-proposal

The draft-proposal command allows users to draft any type of proposal. The command returns a draft_proposal.json, to be used by submit-proposal after being completed. The draft_metadata.json is meant to be uploaded to IPFS.

```Bash
uptickd tx gov draft-proposal

```

#### uptickd tx gov submit-proposal

The submit-proposal command allows users to submit a governance proposal along with some messages and metadata. Messages, metadata and deposit are defined in a JSON file.

```Bash
uptickd tx gov submit-proposal [path/to/proposal.json] [flags]
```

where proposal.json contains:

```JSON
{
    "messages": [
        {
            "@type": "/cosmos.bank.v1beta1.MsgSend",
            "from_address": "uptick1...",// The gov module module address
            "to_address": "uptick1...",
            "amount": [
                {
                    "denom": "uptick",
                    "amount": "10"
                }
            ]
        }
    ],
    "metadata": "AQ==",
    "deposit": "10uptick"
}
```

#### uptickd tx gov submit-legacy-proposal

The submit-legacy-proposal command allows users to submit a governance legacy proposal along with an initial deposit. Proposal title, description, type and deposit can be given directly or through a proposal JSON file. Available Commands: , `client-create`, `client-upgrade`, `relayer-register`, `set-rules`.

<table><thead><tr><th width="309">Name, shorthand</th><th>Description</th></tr></thead><tbody><tr><td>community-pool-spend</td><td>Submit a community pool spend proposal</td></tr><tr><td>param-change</td><td>Submit a parameter change proposal</td></tr><tr><td>software-upgrade</td><td>Submit a software upgrade proposal</td></tr><tr><td>cancel-software-upgrade</td><td>Cancel the current software upgrade proposal</td></tr></tbody></table>

#### uptickd tx gov submit-legacy-proposal community-pool-spend

Submit a community pool spend proposal along with an initial deposit. The proposal details must be supplied via a JSON file.

```Bash
uptickd tx gov submit-legacy-proposal community-pool-spend [proposal-file] [flags]
```

Where proposal.json contains:

```JSON
{
    "title": "Community Pool Spend",
    "description": "Pay me some Atoms!",
    "recipient": "uptick1sual70ma3pltk7zjdf6x4e7m6g3hpg6grm33fa",
    "amount": "1000uptick",
    "deposit": "1000uptick"
}
```

#### uptickd tx gov submit-legacy-proposal param-change

Submit a parameter proposal along with an initial deposit. The proposal details must be supplied via a JSON file. For values that contains objects, only non-empty fields will be updated.IMPORTANT: Currently parameter changes are evaluated but not validated, so it is very important that any "value" change is valid (ie. correct type and within bounds) for its respective parameter, eg. "MaxValidators" should be an integer and not a decimal.Proper vetting of a parameter change proposal should prevent this from happening (no deposits should occur during the governance process), but it should be noted regardless.

```Bash
uptickd tx gov submit-legacy-proposal param-change [proposal-file] [flags]
```

Where proposal.json contains:

```JSON
{
    "title": "Staking Param Change",
    "description": "Update max validators",
    "changes": [
        {
            "subspace": "staking",
            "key": "MaxValidators",
            "value": 105
        }
    ],
    "deposit": "1000uptick"
}
```

#### uptickd tx gov submit-legacy-proposal software-upgrade

Submit a software upgrade along with an initial deposit. Please specify a unique name and height for the upgrade to take effect.

```Bash
uptickd tx gov submit-legacy-proposal software-upgrade [name] (--upgrade-height [height]) (--upgrade-info [info]) [flags]
```

Flags:

<table><thead><tr><th>Name, shorthand</th><th width="98">Type</th><th width="111">Required</th><th width="73">Default</th><th>Description</th></tr></thead><tbody><tr><td>--deposit</td><td>string</td><td>Yes</td><td></td><td>Deposit of the proposal</td></tr><tr><td>--title</td><td>string</td><td>Yes</td><td></td><td>Title of proposal</td></tr><tr><td>--description</td><td>string</td><td>Yes</td><td></td><td>Description of proposal</td></tr><tr><td>--upgrade-height</td><td>int</td><td></td><td></td><td>The height at which the upgrade must happen</td></tr></tbody></table>

#### uptickd tx gov submit-legacy-proposal cancel-software-upgrade

Cancel a software upgrade along with an initial deposit.

```Bash
uptickd tx gov submit-legacy-proposal cancel-software-upgrade [flags]
```


Flags:

| Name, shorthand | Type   | Required | Default | Description             |
| --------------- | ------ | -------- | ------- | ----------------------- |
| --deposit       | string | Yes      |         | Deposit of the proposal |
| --title         | string | Yes      |         | Title of proposal       |
| --description   | string | Yes      |         | Description of proposal |

#### uptickd tx gov deposit

Submit a deposit for an active proposal. You can find the proposal-id by running "uptickd query gov proposals".

```Bash
uptickd tx gov deposit [proposal-id] [deposit] [flags]
```

Deposit for an active proposal

```Bash
uptickd tx gov deposit [proposal-id] [deposit]
```

#### uptickd tx gov vote

Submit a vote for an active proposal. You can find the proposal-id by running "uptickd query gov proposals". Vote for an active proposal, options: yes/no/no_with_veto/abstain.

```Bash
uptickd tx gov vote [proposal-id] [option] [flags]
```

Vote for an active proposal

```Bash
uptickd tx gov vote <proposal-id> <option> --from=<key-name> --fees=0.3uptick
```

#### uptickd tx gov weighted-vote

The weighted-vote command allows users to submit a weighted vote for a given governance proposal.

```Bash
uptickd tx gov weighted-vote [proposal-id] [weighted-options] [flags]
```
