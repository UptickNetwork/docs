# Install Go

{% hint style="info" %}
Uptick is built using [Go ](https://golang.org/dl/)version `1.18+`
{% endhint %}

```
go version
```

{% hint style="info" %}
If the `uptickd: command not found` error message is returned, confirm that your [`GOPATH`](https://golang.org/doc/gopath_code#GOPATH)is correctly configured by running the following command:
{% endhint %}

```sh
mkdir -p $HOME/go/bin
echo "export GOPATH=$HOME/go" >> ~/.bashrc
source ~/.bashrc
echo "export GOBIN=$GOPATH/bin" >> ~/.bashrc
source ~/.bashrc
echo "export PATH=$PATH:$GOBIN" >> ~/.bashrc
source ~/.bashrc
```
