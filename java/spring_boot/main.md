# Spring Boot

## 入门: Spring Boot 黑魔法

### Mac 安装 Spring boot cli

```bash
# 打开 pivotal 公司的水龙头（第三方源）
brew tap pivotal/tap

# 安装
brew install springboot
```

### Hello World!

### app.groovy 内容

```groovy
@RestController
class ThisWillActuallyRun {

    @RequestMapping("/")
    String home() {
        "Hello World!"
    }

}
```

### 运行 app

```bash
# 首次运行会自动下载依赖而等待很久，耐心等待
spring run app.groovy
```

### 完成

成功后输出：

```
Resolving dependencies.................................................................................................................................................................................................................................................................................................................................................................................................................................................

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.2.1.RELEASE)

2019-11-26 23:14:47.893  WARN 19205 --- [       runner-0] o.s.boot.StartupInfoLogger               : InetAddress.getLocalHost().getHostName() took 5005 milliseconds to respond. Please verify your network configuration (macOS machines may need to add entries to /etc/hosts).
2019-11-26 23:14:52.933  INFO 19205 --- [       runner-0] o.s.boot.SpringApplication               : Starting application on FangMac15.local with PID 19205 (started by fang in /Users/fang/Desktop/spring)
2019-11-26 23:14:52.934  INFO 19205 --- [       runner-0] o.s.boot.SpringApplication               : No active profile set, falling back to default profiles: default
2019-11-26 23:14:54.029  INFO 19205 --- [       runner-0] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port(s): 8080 (http)
2019-11-26 23:14:54.046  INFO 19205 --- [       runner-0] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2019-11-26 23:14:54.046  INFO 19205 --- [       runner-0] org.apache.catalina.core.StandardEngine  : Starting Servlet engine: [Apache Tomcat/9.0.27]
2019-11-26 23:14:54.084  INFO 19205 --- [       runner-0] org.apache.catalina.loader.WebappLoader  : Unknown class loader [org.springframework.boot.cli.compiler.ExtendedGroovyClassLoader$DefaultScopeParentClassLoader@72598ebf] of class [class org.springframework.boot.cli.compiler.ExtendedGroovyClassLoader$DefaultScopeParentClassLoader]
2019-11-26 23:14:54.122  INFO 19205 --- [       runner-0] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2019-11-26 23:14:54.122  INFO 19205 --- [       runner-0] o.s.web.context.ContextLoader            : Root WebApplicationContext: initialization completed in 1045 ms
2019-11-26 23:14:54.309  INFO 19205 --- [       runner-0] o.s.s.concurrent.ThreadPoolTaskExecutor  : Initializing ExecutorService 'applicationTaskExecutor'
2019-11-26 23:14:54.811  INFO 19205 --- [       runner-0] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8080 (http) with context path ''
2019-11-26 23:14:54.815  INFO 19205 --- [       runner-0] o.s.boot.SpringApplication               : Started application in 17.45 seconds (JVM running for 1461.705)
2019-11-26 23:19:38.267  INFO 19205 --- [nio-8080-exec-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring DispatcherServlet 'dispatcherServlet'
2019-11-26 23:19:38.267  INFO 19205 --- [nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : Initializing Servlet 'dispatcherServlet'
2019-11-26 23:19:38.277  INFO 19205 --- [nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : Completed initialization in 10 ms
```

进入 [http://localhost:8080/](http://localhost:8080/) 查看成果

## Restful Api

loook up [example](https://github.com/quaeast/simple-restful).

## Security

A simple login [app](https://github.com/quaeast/simple-secure)



