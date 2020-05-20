# Jar



## 创建测试环境

### 建立文件夹

```bash
mkdir testjar	
cd testjar	#进入testjar
mkdir -p src/cn/quaeast
```

### 创建 java 文件

```bash
touch src/cn/quaeast/Main.java
```

### 编写测试代码

```java
package cn.quaeast;

public class Main{
  public static void main(String[] args){
    System.out.println("Hello");
  }
}
```



## 打包

### 编译代码

```bash
javac src/cn/quaeast/Main.java
```

### 创建 MANIFES.MF

```bash
touch MANIFEST.MF
```

内容

```
Main-Class: cn.quaeast.Main
```

### 打包

```bash
# 类似于 tar 命令, 这里的 `-f` 和 `-m` 与后面的参数对应
# `f` 对应 jar 文件, `m` 对应 MANIFEST.MF 文件。
cd src
jar -cvfm main.jar MANIFESR.MF .
```

## 运行

```bash
java -jar main.jar
```

