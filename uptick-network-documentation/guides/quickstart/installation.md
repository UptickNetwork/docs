# Installation

Build and install the Uptick binaries from source or using Docker.

## Pre-requisites

* [Install Go 1.19+](https://golang.org/dl/)
* [Install jq](https://stedolan.github.io/jq/download/)

## Install Go

{% hint style="info" %}
**warning**

Uptick is built using [Go](https://golang.org/dl/) version `1.19+`
{% endhint %}

```bash
go version
```

{% hint style="info" %}
If the `uptickd: command not found` error message is returned, confirm that your [`GOPATH`](https://golang.org/doc/gopath_code#GOPATH) is correctly configured by running the following command:

```bash
mkdir -p $HOME/go/bin
echo "export GOPATH=$HOME/go" >> ~/.bashrc
source ~/.bashrc
echo "export GOBIN=$GOPATH/bin" >> ~/.bashrc
source ~/.bashrc
echo "export PATH=$PATH:$GOBIN" >> ~/.bashrc
source ~/.bashrc
```
{% endhint %}

## Install Binaries

{% hint style="info" %}
The latest Uptick [version](https://github.com/UptickNetwork/uptick/releases) is `v0.3.0`
{% endhint %}

### GitHub

Clone and build Uptick using `git`:

```bash
git clone https://github.com/UptickNetwork/uptick.git
cd uptick
git checkout <version>
make install
```

Check that the `uptickd` binaries have been successfully installed:

```bash
uptickd version
```
