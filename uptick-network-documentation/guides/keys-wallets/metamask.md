# MetaMask

Connect your MetaMask wallet with Uptick

The MetaMask browser extension is a wallet for accessing Ethereum-enabled applications and managing user identities. It can be used to connect to Uptick through the official testnet or via a locally-running Uptick node.

{% hint style="info" %}
If you are planning on developing on Uptick locally and you haven’t already set up your own local node, refer to [the quickstart tutorial](https://github.com/starrymedia/upticknetworkdocs/blob/main/quickstart/run\_node/README.md), or follow the instructions in the [GitHub repository](https://github.com/UptickNetwork/uptick/).
{% endhint %}

## Adding a New Network

Open the MetaMask extension on your browser, you may have to log in to your MetaMask account if you are not already. Then click the top right circle and go to `Settings` > `Networks` > `Add Network` and fill the form as shown below.

{% hint style="info" %}
You can also lookup the [EIP155](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md) `Chain ID` by referring to [chainlist.org](https://chainlist.org/). Alternatively, to get the full Chain ID from Genesis, check the [Chain ID](https://github.com/starrymedia/upticknetworkdocs/blob/main/basics/chain\_id/README.md) documentation page.
{% endhint %}

![metamask networks settings](../../.gitbook/assets/metamask\_network\_settings.png)

Here is the list of fields that you can use to paste on Metamask:

Testnet

* **Network Name:** `Uptick Testnet`
* **New RPC URL:** `{{ $themeConfig.project.rpc_url_testnet }}`
* **Chain ID:** `7000`
* **Currency Symbol (optional):** `{{ $themeConfig.project.testnet_ticker }}`
* **Block Explorer URL (optional):** `{{ $themeConfig.project.block_explorer_url }}`

Local Node

* **Network Name:** `Uptick Local`
* **New RPC URL:** `{{ $themeConfig.project.rpc_url_local }}`
* **Chain ID:** `7000`
* **Currency Symbol (optional):** `{{ $themeConfig.project.testnet_ticker }}`
* **Block Explorer URL (optional):** `n/a`

## Import Account to Metamask

### Manual Import

Close the `Settings`, go to `My Accounts` (top right circle) and select `Import Account`. You should see an image like the following one:

![metamask manual import account page](../../.gitbook/assets/metamask\_import.png)

Now you can export your private key from the terminal using the following command. Again, make sure to replace `mykey` with the name of the key that you want to export and use the correct `keyring-backend`:

```bash
uptickd keys unsafe-export-eth-key mykey --keyring-backend test
```

Go back to the browser and select the `Private Key` option. Then paste the private key exported from the `unsafe-export-eth-key` command.

Your account balance should show up as `1 {{ $themeConfig.project.testnet_ticker }}` and do transfers as usual.

{% hint style="info" %}
If it takes some time to load the balance of the account, change the network to `Main Ethereum Network` (or any other than `Localhost 8545` or `Uptick`) and then switch back to `Uptick`.
{% endhint %}

## Reset Account

If you used your Metamask account for a legacy testnet/mainnet upgrade, you will need to reset your account in order to use it with the new network. This will clear your account's transaction history, but it won't change the balances in your accounts or require you to re-enter your `Secret Recovery Phrase`.

:

{% hint style="info" %}
Make sure you download your [account state](metamask.md#download-account-state) to persist public account addresses and transactions before clearing your wallet accounts.
{% endhint %}

Go to `Settings` > `Advanced` and click the `Reset Account` button as shown below:

![Metamask Account Reset](../../.gitbook/assets/reset\_account.png)

## Download Account State

To see your Metamask logs, click the top right circle and go to `Settings` > `Advanced` > `State Logs`. If you search through the JSON file for the account address you'll find the transaction history.
