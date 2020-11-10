# ssh 配置方法

## 客户端

### 生成秘钥

```bash
ssh-keygen -t rsa -b 4096 -C "xxxxxx@email.com"
```

### 更改权限

```bash
chmod 400 private_key
```

注意这里一定要把其他人的权限去掉，否则可能会连接失败。我之前一直没办法用秘钥连接阿里云的服务器，就是这个原因。

### ~/.ssh/config 模板

```bash
Host github.com
    HostName github.com
    User 424044876@qq.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/private_key
```

```bash
Host alc
    HostName x.x.x.x
    User root
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/private_key
```

```bash
Host da
    HostName x.x.x.x
    User qua
    PreferredAuthentications password
```

## 服务器端

### 公钥添加位置

```bash
~/.ssh/authorized_keys
```

### 配置选项 /etc/ssh/sshd_config

```
# 秘钥登录
RSAAuthentication yes
PubkeyAuthentication yes

# root远程登录
PermitRootLogin yes

# 密码登录
PasswordAuthentication no
```
### 重启服务

```bash
service sshd restart
```


