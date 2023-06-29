# API Port, Activation and Configuration


All routes are configured under the following fields in ~/.uptick/config/app.toml:

api.enable = true|false field defines if the REST server should be enabled. Defaults to true.
api.address = {string} field defines the address (really, the port, since the host should be kept at 0.0.0.0) the server should bind to. Defaults to tcp://0.0.0.0:1317.
some additional API configuration options are defined in ~/.uptick/config/app.toml, along with comments, please refer to that file directly.
