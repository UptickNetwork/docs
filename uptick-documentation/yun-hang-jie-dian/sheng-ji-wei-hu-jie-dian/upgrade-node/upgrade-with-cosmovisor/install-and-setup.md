# Install and Setup

To get started with [Cosmovisor (opens new window)](https://github.com/cosmos/cosmos-sdk/tree/master/cosmovisor)first download it

```sh
go get github.com/cosmos/cosmos-sdk/cosmovisor/cmd/cosmovisor
```

Set up the Cosmovisor environment variables. We recommend setting these in your `.profile` so it is automatically set in every session.&#x20;

```sh
echo "# Setup Cosmovisor" >> ~/.profile
echo "export DAEMON_NAME=uptickd" >> ~/.profile
echo "export DAEMON_HOME=$HOME/.uptickd" >> ~/.profile
echo 'export PATH="$DAEMON_HOME/cosmovisor/current/bin:$PATH"' >> ~/.profile
source ~/.profile
```

After this, you must make the necessary folders for cosmosvisor in your daemon home directory (\~/.uptickd).

```sh
mkdir -p ~/.uptickd/cosmovisor/upgrades
mkdir -p ~/.uptickd/cosmovisor/genesis/bin
cp $(which uptickd) ~/.uptickd/cosmovisor/genesis/bin/

# Verify the setup
# It should return the same version as uptickd
cosmovisor version
```
