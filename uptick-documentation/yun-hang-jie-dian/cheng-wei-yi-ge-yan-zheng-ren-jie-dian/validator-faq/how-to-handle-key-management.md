# How to handle key management?

Validators should expect to run an HSM that supports ed25519 keys. Here are potential options:

* YubiHSM 2
* Ledger Nano S
* Ledger BOLOS SGX enclave
* Thales nShield support
* [Strangelove Horocrux](https://github.com/strangelove-ventures/horcrux)

The Uptick team does not recommend one solution above the other. The community is encouraged to bolster the effort to improve HSMs and the security of key management.
