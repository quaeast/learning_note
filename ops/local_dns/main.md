# 本地 DNS：解决 github.com 不可访问

## 解决

为 `/etc/hosts` 添加三条解析，通过 [ipaddress](https://www.ipaddress.com/) 查询

```
192.30.253.112 github.com

151.101.184.133 assets-cdn.github.com

151.101.185.194 github.global.ssl.fastly.net
```

## Unix 关于 DNS 的设置

优先级 1>2>3

### 1. HOST 本地 DNS 解析

```bash
vim /etc/hosts
```

```
127.0.0.1	localhost
```

### 2. 网卡配置文件DNS服务地址 

```bash
vim /etc/sysconfig/network-scripts/ifcfg-eth0
```

```
DSN1='114.114.114.114'
```

### 3. 系统默认DNS配置

```bash
vim /etc/resolv.conf
```

```
nameserver 8.8.8.8
```