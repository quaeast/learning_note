# crontab

## 基本命令

```sh
# list
crontab -l

# remove
crontab -r

# edit
crontab -e

# add
crontab <filename>
```

## 文件格式

![](/Users/fang/Desktop/git_repos/learning_note/crontab/img/crontab-layout.png)

## log

修改 `/etc/rsyslog.d/50-default.conf` 

对这一行解除注释

```
cron.*                          /var/log/cron.log
```

```sh
# 重启 rsyslog
sudo service rsyslog restart

# 查看 log
less /var/log/cron.log 
```