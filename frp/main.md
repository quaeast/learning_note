# [frp](https://github.com/fatedier/frp)

frp 是一个内网穿透的工具，这个软件分为两个部分，一部分是客户端（frpc），一部分是服务端（frps）。前者搭建在需要被映射 ip 的服务器上，后者搭建在具有公网 ip 地址的服务器上。

## ssh

### frp 配置

frp 配置只需要两步

配置 ip 服务器的 `frps.ini`

```ini
[common]
bind_port = 7000
```

启动命令：

```shell
frps -c frps.ini
```

配置需要被映射的服务器的 frpc.ini

```ini
[common]
server_addr = x.x.x.x
server_port = 7000

[ssh]
type = tcp
local_ip = 127.0.0.1
local_port = 22
remote_port = 6000
```

启动命令：

```shell
frps -c frps.ini
```

### 将程序挂在 systemd

添加 `/etc/systemd/system/xxx.service`

```ini
[Unit]
Description=Frp Server Service
After=network.target

[Service]
Type=simple
User=fang
Restart=on-failure
RestartSec=5s
ExecStart=/usr/bin/frps -c /etc/frp/frps.ini

[Install]
WantedBy=multi-user.target
```

导入配置

```shell
# 启动
systemctl start|stop|restart xxx.service
# 添加开机启动
systemctl enable|disable xxx.service
# list
systemctl list-units --type=service
```

### 对于 Mac 需要挂在 launchd 

添加文件 `~/Library/LaunchAgents/xxx.plist`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
    <dict>
        <key>Label</key>
        <string>frp</string>
        <key>WorkingDirectory</key>
        <string>/Users/fang/frp/frp_0.34.1_darwin_amd64</string>
        <key>ProgramArguments</key>
        <array>
            <string>./frpc</string>
            <string>-c</string>
            <string>frpc.ini</string>
        </array>
        <key>StandardOutPath</key>
        <string>frpc.log</string>
        <key>StandardErrorPath</key>
        <string>frpc.log</string>
        <key>RunAtLoad</key>
        <true/>
    </dict>
</plist>
```

启动

```shell
# 装在配置文件，放在这个文件夹里是可以开机自动扫描的
launchctl load ~/Library/LaunchAgents/xxx.plist
# 检查运行状态
launchctl list | grep frp
```

* [systemd](https://quaeast.cn/service/main.html#mac-brew-services) 上手参考
* [launchd](https://www.launchd.info/) 上手参考
* [frp github](https://github.com/fatedier/frp)

