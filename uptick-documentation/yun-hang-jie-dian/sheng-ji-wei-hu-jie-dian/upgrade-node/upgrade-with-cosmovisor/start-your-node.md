# Start your node

Now that everything is setup and ready to go, you can start your node.

```
cosmovisor start
```

You will need some way to keep the process always running. If you're on linux, you can do this by creating a service.

```sh
sudo tee /etc/systemd/system/uptickd.service > /dev/null <<EOF
[Unit]
Description=Uptick Daemon
After=network-online.target

[Service]
User=$USER
ExecStart=$(which cosmovisor) start
Restart=always
RestartSec=3
LimitNOFILE=infinity

Environment="DAEMON_HOME=$HOME/.uptickd"
Environment="DAEMON_NAME=uptickd"
Environment="DAEMON_ALLOW_DOWNLOAD_BINARIES=false"
Environment="DAEMON_RESTART_AFTER_UPGRADE=true"

[Install]
WantedBy=multi-user.target
EOF
```

Then update and start the node

```sh
sudo -S systemctl daemon-reload
sudo -S systemctl enable uptickd
sudo -S systemctl start uptickd
```

You can check the status with:

```sh
systemctl status uptickd
```
