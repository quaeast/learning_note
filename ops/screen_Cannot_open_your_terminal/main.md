# screen Cannot open your terminal '/dev/pst/1'


## 解决

这个问题由于登录系统后切换用户引起。解决如下：

```bash
script /dev/null
```

## 原理

### 问题产生原因

切换用户之后并没有创建新的 tty ，而这个 tty 的所有权还是原来用户，所以 screen 无法操作。

所以解决问题的思路就是：新创建一个属于当前用户的 tty。

验证
```
(base) ➜  ~ tty
/dev/ttys004
(base) ➜  ~ su
Password:
sh-3.2# tty
/dev/ttys004
sh-3.2#
```

### script /dev/null

`script` 是用来录屏的命令。在运行时会先创建一个新的tty，把录屏的数据存放到后面的参数里。这样问题就解决了。

验证
```
(base) ➜  ~ tty
/dev/ttys006
(base) ➜  ~ script /dev/null
Script started, output file is /dev/null
(base) ➜  ~ tty
/dev/ttys004
(base) ➜  ~ exit

Script done, output file is /dev/null
(base) ➜  ~ tty
/dev/ttys006
(base) ➜  ~
```

