# Cosmovisor

`cosmovisor` is a small process manager for Cosmos SDK application binaries that monitors the governance module for incoming chain upgrade proposals. If it sees a proposal that gets approved, `cosmovisor` can automatically download the new binary, stop the current binary, switch from the old binary to the new one, and finally restart the node with the new binary.

* [Setup](cosmovisor.md#setup)
  * [Installation](cosmovisor.md#installation)
  * [Command Line Arguments And Environment Variables](cosmovisor.md#command-line-arguments-and-environment-variables)
  * [Folder Layout](cosmovisor.md#folder-layout)
* [Usage](cosmovisor.md#usage)
  * [Initialization](cosmovisor.md#initialization)
  * [Detecting Upgrades](cosmovisor.md#detecting-upgrades)
  * [Auto-Download](cosmovisor.md#auto-download)
* [Example: SimApp Upgrade](cosmovisor.md#example-simapp-upgrade)
  * [Chain Setup](cosmovisor.md#chain-setup)

## Setup

### Installation

To install the latest version of `cosmovisor`, run the following command:

```sh
go install github.com/cosmos/cosmos-sdk/cosmovisor/cmd/cosmovisor@latest
```

To install a previous version, you can specify the version. IMPORTANT: Chains that use uptick v0.1.0 and want to use auto-download feature MUST use Cosmovisor v0.1.0

```sh
go install github.com/cosmos/cosmos-sdk/cosmovisor/cmd/cosmovisor@v0.1.0
```

You can run `cosmovisor version` to check the Cosmovisor version (works only with Cosmovisor >1.1.0).

You can also install from source by pulling the cosmos-sdk repository and switching to the correct version and building as follows:

```sh
git clone git@github.com:cosmos/cosmos-sdk
cd cosmos-sdk
git checkout cosmovisor/vx.x.x
make cosmovisor
```

This will build cosmovisor in `/cosmovisor` directory. Afterwards you may want to put it into your machine's PATH like as follows:

```sh
cp cosmovisor/cosmovisor ~/go/bin/cosmovisor
```

_Note: If you are using go `v1.15` or earlier, you will need to use `go get`, and you may want to run the command outside a project directory._

### Command Line Arguments And Environment Variables

The first argument passed to `cosmovisor` is the action for `cosmovisor` to take. Options are:

* `help`, `--help`, or `-h` - Output `cosmovisor` help information and check your `cosmovisor` configuration.
* `run` - Run the configured binary using the rest of the provided arguments.
* `version` - Output the `cosmovisor` version and also run the binary with the `version` argument.

All arguments passed to `cosmovisor run` will be passed to the application binary (as a subprocess). `cosmovisor` will return `/dev/stdout` and `/dev/stderr` of the subprocess as its own. For this reason, `cosmovisor run` cannot accept any command-line arguments other than those available to the application binary.

*Note: Use of `cosmovisor` without one of the action arguments is deprecated. For backwards compatibility, if the first argument is not an action argument, `run` is assumed. However, this fallback might be removed in future versions, so it is recommended that you always provide `run`.

`cosmovisor` reads its configuration from environment variables:

* `DAEMON_HOME` is the location where the `cosmovisor/` directory is kept that contains the genesis binary, the upgrade binaries, and any additional auxiliary files associated with each binary (e.g. `$HOME/.gaiad`, `$HOME/.uptickd`, `$HOME/.simd`, etc.).
* `DAEMON_NAME` is the name of the binary itself (e.g. `gaiad`, `uptickd`, `simd`, etc.).
* `DAEMON_ALLOW_DOWNLOAD_BINARIES` (_optional_), if set to `true`, will enable auto-downloading of new binaries (for security reasons, this is intended for full nodes rather than validators). By default, `cosmovisor` will not auto-download new binaries.
* `DAEMON_RESTART_AFTER_UPGRADE` (_optional_, default = `true`), if `true`, restarts the subprocess with the same command-line arguments and flags (but with the new binary) after a successful upgrade. Otherwise (`false`), `cosmovisor` stops running after an upgrade and requires the system administrator to manually restart it. Note restart is only after the upgrade and does not auto-restart the subprocess after an error occurs.
* `DAEMON_RESTART_DELAY` (_optional_, default none), allow a node operator to define a delay between the node halt (for upgrade) and backup by the specified time. The value must be a duration (e.g. `1s`).
* `DAEMON_POLL_INTERVAL` (_optional_, default 300 milliseconds), is the interval length for polling the upgrade plan file. The value must be a duration (e.g. `1s`).
* `DAEMON_DATA_BACKUP_DIR` option to set a custom backup directory. If not set, `DAEMON_HOME` is used.
* `UNSAFE_SKIP_BACKUP` (defaults to `false`), if set to `true`, upgrades directly without performing a backup. Otherwise (`false`, default) backs up the data before trying the upgrade. The default value of false is useful and recommended in case of failures and when a backup needed to rollback. We recommend using the default backup option `UNSAFE_SKIP_BACKUP=false`.
* `DAEMON_PREUPGRADE_MAX_RETRIES` (defaults to `0`). The maximum number of times to call `pre-upgrade` in the application after exit status of `31`. After the maximum number of retries, cosmovisor fails the upgrade.

### Folder Layout

`$DAEMON_HOME/cosmovisor` is expected to belong completely to `cosmovisor` and the subprocesses that are controlled by it. The folder content is organized as follows:

```
.
├── current -> genesis or upgrades/<name>
├── genesis
│   └── bin
│       └── $DAEMON_NAME
└── upgrades
    └── <name>
        ├── bin
        │   └── $DAEMON_NAME
        └── upgrade-info.json
```

The `cosmovisor/` directory incudes a subdirectory for each version of the application (i.e. `genesis` or `upgrades/<name>`). Within each subdirectory is the application binary (i.e. `bin/$DAEMON_NAME`) and any additional auxiliary files associated with each binary. `current` is a symbolic link to the currently active directory (i.e. `genesis` or `upgrades/<name>`). The `name` variable in `upgrades/<name>` is the URI-encoded name of the upgrade as specified in the upgrade module plan.

Please note that `$DAEMON_HOME/cosmovisor` only stores the _application binaries_. The `cosmovisor` binary itself can be stored in any typical location (e.g. `/usr/local/bin`). The application will continue to store its data in the default data directory (e.g. `$HOME/.gaiad`) or the data directory specified with the `--home` flag. `$DAEMON_HOME` is independent of the data directory and can be set to any location. If you set `$DAEMON_HOME` to the same directory as the data directory, you will end up with a configuation like the following:

```
.uptickd
├── config
├── data
└── cosmovisor
```

## Usage

The system administrator is responsible for:

* installing the `cosmovisor` binary
* configuring the host's init system (e.g. `systemd`, `launchd`, etc.)
* appropriately setting the environmental variables
* creating the `<DAEMON_HOME>/cosmovisor` directory
* creating the `<DAEMON_HOME>/cosmovisor/genesis/bin` folder
* creating the `<DAEMON_HOME>/cosmovisor/upgrades/<name>/bin` folders
* placing the different versions of the `<DAEMON_NAME>` executable in the appropriate `bin` folders.

`cosmovisor` will set the `current` link to point to `genesis` at first start (i.e. when no `current` link exists) and then handle switching binaries at the correct points in time so that the system administrator can prepare days in advance and relax at upgrade time.

In order to support downloadable binaries, a tarball for each upgrade binary will need to be packaged up and made available through a canonical URL. Additionally, a tarball that includes the genesis binary and all available upgrade binaries can be packaged up and made available so that all the necessary binaries required to sync a fullnode from start can be easily downloaded.

The `DAEMON` specific code and operations (e.g. tendermint config, the application db, syncing blocks, etc.) all work as expected. The application binaries' directives such as command-line flags and environment variables also work as expected.

### Initialization

The `cosmovisor init <path to executable>` command creates the folder structure required for using cosmovisor.

It does the following:

* creates the `<DAEMON_HOME>/cosmovisor` folder if it doesn't yet exist
* creates the `<DAEMON_HOME>/cosmovisor/genesis/bin` folder if it doesn't yet exist
* copies the provided executable file to `<DAEMON_HOME>/cosmovisor/genesis/bin/<DAEMON_NAME>`
* creates the `current` link, pointing to the `genesis` folder

It uses the `DAEMON_HOME` and `DAEMON_NAME` environment variables for folder location and executable name.

The `cosmovisor init` command is specifically for initializing cosmovisor, and should not be confused with a chain's `init` command (e.g. `cosmovisor run init`).

### Detecting Upgrades

`cosmovisor` is polling the `$DAEMON_HOME/data/upgrade-info.json` file for new upgrade instructions. The file is created by the x/upgrade module in `BeginBlocker` when an upgrade is detected and the blockchain reaches the upgrade height. The following heuristic is applied to detect the upgrade:

* When starting, `cosmovisor` doesn't know much about currently running upgrade, except the binary which is `current/bin/`. It tries to read the `current/update-info.json` file to get information about the current upgrade name.
* If neither `cosmovisor/current/upgrade-info.json` nor `data/upgrade-info.json` exist, then `cosmovisor` will wait for `data/upgrade-info.json` file to trigger an upgrade.
* If `cosmovisor/current/upgrade-info.json` doesn't exist but `data/upgrade-info.json` exists, then `cosmovisor` assumes that whatever is in `data/upgrade-info.json` is a valid upgrade request. In this case `cosmovisor` tries immediately to make an upgrade according to the `name` attribute in `data/upgrade-info.json`.
* Otherwise, `cosmovisor` waits for changes in `upgrade-info.json`. As soon as a new upgrade name is recorded in the file, `cosmovisor` will trigger an upgrade mechanism.

When the upgrade mechanism is triggered, `cosmovisor` will:

1. if `DAEMON_ALLOW_DOWNLOAD_BINARIES` is enabled, start by auto-downloading a new binary into `cosmovisor/<name>/bin` (where `<name>` is the `upgrade-info.json:name` attribute);
2. update the `current` symbolic link to point to the new directory and save `data/upgrade-info.json` to `cosmovisor/current/upgrade-info.json`.

### Auto-Download

Generally, `cosmovisor` requires that the system administrator place all relevant binaries on disk before the upgrade happens. However, for people who don't need such control and want an automated setup (maybe they are syncing a non-validating fullnode and want to do little maintenance), there is another option.

**NOTE: we don't recommend using auto-download** because it doesn't verify in advance if a binary is available. If there will be any issue with downloading a binary, the cosmovisor will stop and won't restart an App (which could lead to a chain halt).

If `DAEMON_ALLOW_DOWNLOAD_BINARIES` is set to `true`, and no local binary can be found when an upgrade is triggered, `cosmovisor` will attempt to download and install the binary itself based on the instructions in the `info` attribute in the `data/upgrade-info.json` file. The files is constructed by the x/upgrade module and contains data from the upgrade `Plan` object. The `Plan` has an info field that is expected to have one of the following two valid formats to specify a download:

1.  Store an os/architecture -> binary URI map in the upgrade plan info field as JSON under the `"binaries"` key. For example:

    ```json
    {
      "binaries": {
        "linux/amd64":"https://example.com/gaia.zip?checksum=sha256:aec070645fe53ee3b3763059376134f058cc337247c978add178b6ccdfb0019f"
      }
    }
    ```

    You can include multiple binaries at once to ensure more than one environment will receive the correct binaries:

    ```json
    {
      "binaries": {
        "linux/amd64":"https://example.com/gaia.zip?checksum=sha256:aec070645fe53ee3b3763059376134f058cc337247c978add178b6ccdfb0019f",
        "linux/arm64":"https://example.com/gaia.zip?checksum=sha256:aec070645fe53ee3b3763059376134f058cc337247c978add178b6ccdfb0019f",
        "darwin/amd64":"https://example.com/gaia.zip?checksum=sha256:aec070645fe53ee3b3763059376134f058cc337247c978add178b6ccdfb0019f"
        }
    }
    ```

    When submitting this as a proposal ensure there are no spaces. An example command using `gaiad` could look like:

    ```sh
    > gaiad tx gov submit-proposal software-upgrade Vega \
    --title Vega \
    --deposit 100uatom \
    --upgrade-height 7368420 \
    --upgrade-info '{"binaries":{"linux/amd64":"https://github.com/cosmos/gaia/releases/download/v6.0.0-rc1/gaiad-v6.0.0-rc1-linux-amd64","linux/arm64":"https://github.com/cosmos/gaia/releases/download/v6.0.0-rc1/gaiad-v6.0.0-rc1-linux-arm64","darwin/amd64":"https://github.com/cosmos/gaia/releases/download/v6.0.0-rc1/gaiad-v6.0.0-rc1-darwin-amd64"}}' \
    --description "upgrade to Vega" \
    --gas 400000 \
    --from user \
    --chain-id test \
    --home test/val2 \
    --node tcp://localhost:36657 \
    --yes
    ```
2.  Store a link to a file that contains all information in the above format (e.g. if you want to specify lots of binaries, changelog info, etc. without filling up the blockchain). For example:

    ```
    https://example.com/testnet-1001-info.json?checksum=sha256:deaaa99fda9407c4dbe1d04bd49bab0cc3c1dd76fa392cd55a9425be074af01e
    ```

When `cosmovisor` is triggered to download the new binary, `cosmovisor` will parse the `"binaries"` field, download the new binary with [go-getter](https://github.com/hashicorp/go-getter), and unpack the new binary in the `upgrades/<name>` folder so that it can be run as if it was installed manually.

Note that for this mechanism to provide strong security guarantees, all URLs should include a SHA 256/512 checksum. This ensures that no false binary is run, even if someone hacks the server or hijacks the DNS. `go-getter` will always ensure the downloaded file matches the checksum if it is provided. `go-getter` will also handle unpacking archives into directories (in this case the download link should point to a `zip` file of all data in the `bin` directory).

To properly create a sha256 checksum on linux, you can use the `sha256sum` utility. For example:

```sh
sha256sum ./testdata/repo/zip_directory/autod.zip
```

The result will look something like the following: `29139e1381b8177aec909fab9a75d11381cab5adf7d3af0c05ff1c9c117743a7`.

You can also use `sha512sum` if you would prefer to use longer hashes, or `md5sum` if you would prefer to use broken hashes. Whichever you choose, make sure to set the hash algorithm properly in the checksum argument to the URL.

## Example: Uptick Upgrade

The following instructions provide a demonstration of `cosmovisor` using the uptick application (`uptickd`) shipped with the Cosmos SDK's source code. The following commands are to be run from within the `cosmos-sdk` repository.

### Install Cosmovisor

```sh
git clone git@github.com:cosmos/cosmos-sdk
cd cosmos-sdk
make cosmovisor
```

### Chain Setup

Let's create a new chain using the `v0.1.0` version of uptickd:

```sh
git clone https://github.com/UptickNetwork/uptick.git
cd uptick
git checkout v0.1.0
make build
```

Clean `~/.uptickd` (never do this in a production environment):

```sh
./build/uptickd tendermint unsafe-reset-all
```

Set up app config:

```sh
./build/uptickd config chain-id origin_1170-1
./build/uptickd config keyring-backend test
./build/uptickd config broadcast-mode block
```

Initialize the node and overwrite any previous genesis file (never do this in a production environment):

```sh
./build/uptickd testnet init-files --chain-id origin_1170-1 --keyring-backend test --v 1 --output-dir ./.mytestnet
cp -r .mytestnet/node0/uptickd/ ~/.uptickd/
```

For the sake of this demonstration, amend `voting_period` in `genesis.json` to a reduced time of 20 seconds (`20s`):

```sh
cat <<< $(jq '.app_state.gov.voting_params.voting_period = "20s"' ~/.uptickd/config/genesis.json) > ~/.uptickd/config/genesis.json
```

#### Prepare Cosmovisor and Start the Chain

Set the required environment variables:

```sh
export DAEMON_NAME=uptickd
export DAEMON_HOME=~/.uptickd
```

Set the optional environment variable to trigger an automatic app restart:

```sh
export DAEMON_RESTART_AFTER_UPGRADE=true
```

Create the folder for the genesis binary and copy the `uptickd` binary:

```sh
mkdir -p $DAEMON_HOME/cosmovisor/genesis/bin
cp ./build/uptickd $DAEMON_HOME/cosmovisor/genesis/bin
```

Now you can run cosmovisor with uptickd v0.1.0:

```sh
nohup cosmovisor run start --home $DAEMON_HOME > $DAEMON_HOME/cosmovisor/node.log 2>&1 & 
```

#### Update App

Update app to the latest version (e.g. v0.2.0).

Next, we can add a migration - which is defined using `x/upgrade` [upgrade plan](https://github.com/cosmos/cosmos-sdk/blob/main/docs/core/upgrade.md) (you may refer to a past version if you are using an older Cosmos SDK release). In a migration we can do any deterministic state change.

Build the new version `uptickd` binary:

```sh
git checkout v0.2.0
make build
```

Create the folder for the upgrade binary and copy the `uptickd` binary:

```sh
mkdir -p $DAEMON_HOME/cosmovisor/upgrades/v0.2/bin
cp ./build/uptickd $DAEMON_HOME/cosmovisor/upgrades/v0.2/bin
```

Open a new terminal window and submit an upgrade proposal along with a deposit and a vote (these commands must be run within 20 seconds of each other):

```sh
./build/uptickd tx gov submit-proposal software-upgrade v0.2 --title upgrade --description upgrade --upgrade-height 50 --from node0 --yes --keyring-backend test --keyring-dir ~/.uptickd --chain-id origin_1170-1 -b block

./build/uptickd tx gov deposit 1 100000000000000000auptick -y --from node0 --yes --keyring-backend test --keyring-dir ~/.uptickd --chain-id origin_1170-1 -b block

./build/uptickd tx gov vote 1 yes --from node0 --yes --keyring-backend test --keyring-dir ~/.uptickd --chain-id origin_1170-1 -b block
```

### check log

```sh
tail -n 100 -f $DAEMON_HOME/cosmovisor/node.log
```

The upgrade will occur automatically at height 50. Note: you may need to change the upgrade height in the snippet above if your test play takes more time.
