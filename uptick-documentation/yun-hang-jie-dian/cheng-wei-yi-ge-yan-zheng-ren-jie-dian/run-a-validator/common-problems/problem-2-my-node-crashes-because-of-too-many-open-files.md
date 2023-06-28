# Problem #2: My node crashes because of too many open files

The default number of files Linux can open (per-process) is `1024`. `uptickd` is known to open more than `1024` files. This causes the process to crash. A quick fix is to run `ulimit -n 4096` (increase the number of open files allowed) and then restart the process with `uptickd start`. If you are using `systemd` or another process manager to launch `uptickd` this may require some configuration at that level. A sample `systemd` file to fix this issue is below:

```sh
# /etc/systemd/system/uptickd.service
[Unit]
Description=Uptick Node
After=network.target

[Service]
Type=simple
User=ubuntu
WorkingDirectory=/home/ubuntu
ExecStart=/home/ubuntu/go/bin/uptickd start
Restart=on-failure
RestartSec=3
LimitNOFILE=4096

[Install]
WantedBy=multi-user.target
```
