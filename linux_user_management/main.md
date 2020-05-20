# Linux 用户管理

## 内容

### 查看

```sh
cat /etc/group
cat /etc/passwd
cat /etc/shadow
```

### 创建和删除

```sh
# 创建主目录等相应配套
adduser Username
# 只添加用户
useradd Username

# 删除主目录等相应配套
deluser Username
# 只删除用户
userdel Username
```

### 修改密码

```sh
passwd Username
```

### 添加 sudoer

在 `/etc/sudoers` 中添加，主义先 `chmod u+w /etc/sudoers`

```
Username	ALL=(ALL:ALL) ALL
```

