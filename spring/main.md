# Spring

## Spring boot 入门黑魔法

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
