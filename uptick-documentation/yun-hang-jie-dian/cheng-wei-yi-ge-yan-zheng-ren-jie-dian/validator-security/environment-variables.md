# Environment Variables

By default, uppercase environment variables with the following prefixes will replace lowercase command-line flags:

* `UPTICK` (for Uptick flags)
* `TM` (for Tendermint flags)
* `BC` (for democli or basecli flags)

For example, the environment variable `UPTICK_CHAIN_ID` will map to the command line flag `--chain-id`. Note that while explicit command-line flags will take precedence over environment variables, environment variables will take precedence over any of your configuration files. For this reason, it's imperative that you lock down your environment such that any critical parameters are defined as flags on the binary or prevent modification of any environment variables.
