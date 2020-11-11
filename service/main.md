# Service 后台服务管理

## Mac: brew services

```bash
# 显示服务信息
brew services list
```

## Linux: service

```bash
# 显示服务信息
service --status-all
```

## Linux service 添加服务

需要是用 `systemctl` 命令

首先创建服务描述文件：`/etc/systemd/system/service_name.service`

```
[Unit]
Description=ndoejs static website
After=network.target
StartLimitIntervalSec=0
[Service]
Type=simple
Restart=always
RestartSec=1
User=fang
ExecStart=/usr/local/nodejs/bin/node service.js

[Install]
WantedBy=multi-user.target
```

```sh
# 启动
systemctl start|stop|restart xxx.service
# 添加开机启动
systemctl enable|disable xxx.service
# list
systemctl list-units --type=service
```

