# PostgreSql 安装及远程连接



## 安装

### 安装

```bash
# ubuntu
sudo apt install postgresql
# mac 版本可以使用图形界面版本
```

### 测试

```
nmap localhost
```

输出结果如下，出现 `5432/tcp open  postgresql` ，证明启动成功。

```
Starting Nmap 7.60 ( https://nmap.org ) at 2020-01-16 17:37 CST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0000070s latency).
Other addresses for localhost (not scanned): ::1
Not shown: 998 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
5432/tcp open  postgresql

Nmap done: 1 IP address (1 host up) scanned in 1.64 seconds
```

### 设置密码

安装成功后会默认生成一个名为 postgres 的系统用户和数据库用户。

```bash
# 切换用户
sudo su - postgres
# 进入命令行
psql

```

```sql
-- 设置该用户的密码
\password postgres
```

### 远程配置

修改  `/etc/postgresql/10/main/postgresql.conf` 

```
listen_addresses = '*'
```


修改 `pg_hba.conf` ，在其中添加一行

```
host all all all md5
```

## 远程测试

### 远程端口扫描

```bash
namp [your remote server ip]
```

### Jdbc 连接测试

创建 maven 项目，`pom.xml`添加依赖（添加依赖的教程可以查看 [maven教程](../maven/main.md)）：

下面是 java8 以上的 postgre 驱动，更低版本的参见官方 [github](https://github.com/pgjdbc/pgjdbc)

运行程序，没有输出，即安装成功。

```xml
</dependencies>
    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
        <version>42.2.9</version>
    </dependency>
</dependencies>
```

```java
package cn.quaeast;


import java.sql.Connection;
import java.sql.Driver;
import java.sql.SQLException;
import java.util.Properties;

public class TestJdbc {
    static String url = "jdbc:postgresql://x.x.x.143:5432/postgres";

    static String user = "postgres";

    static String password = "password";

    public static void main(String[] args)  {
        Driver driver = new org.postgresql.Driver();

        Properties properties = new Properties();
        properties.setProperty("user", user);
        properties.setProperty("password", password);


        try {
            Connection connection = driver.connect(url, properties);
        } catch (SQLException e) {
            System.out.println("error");
            e.printStackTrace();
        }

    }
}
```