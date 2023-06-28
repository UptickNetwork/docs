# Software Upgrade

These instructions are for full nodes that have ran on previous versions of and would like to upgrade to the latest testnet.

First, stop your instance of `uptickd`. Next, upgrade the software:

```sh
cd uptick
git fetch --all && git checkout <new_version>
make install
```

{% hint style="info" %}
If you have issues at this step, please check that you have the latest stable version of GO installed.
{% endhint %}

You will need to ensure that the version installed matches the one needed for th testnet. Check the Uptick [release page ](https://github.com/UptickNetwork/uptick/releases)for details on each release.

Verify that everything is OK. If you get something like the following, you've successfully installed Uptick on your system.

```sh
$ uptickd version --long

name: uptick
server_name: uptickd
version: 0.1.0
commit: d477e775a2596701ea215a4570e8ea9669d76edf
build_tags: netgo,ledger
go: go version go1.17 darwin/amd64
...
```

If the software version does not match, then please check your $PATH to ensure the correct uptickd is running.
