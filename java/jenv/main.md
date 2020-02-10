# jenv

## Mac JDK 路径

```
/Library/Java/JavaVirtualMachines
```

安装Jdk: 直接从 Oracle 下载 Jdk 解压之后放到这个文件夹下面即可。

环境变量配置与切换：使用 jenv 。

## jenv 安装 

### brew

```zsh
brew install jenv
```

### git clone

或者采用 git clone 从 github 上安装

[jenv.be](https://www.jenv.be/)

```zsh
git clone https://github.com/gcuisinier/jenv.git ~/.jenv
```

### 配置

在 .zshrc 或者 .bash_profile 中加入一下内容完成配置

```bash
export PATH="$HOME/.jenv/bin:$PATH"
eval "$(jenv init -)"
```

## jenv 使用

```zsh
# 添加
jenv add /System/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home

# 列表
jenv versions

# 展示当前
jenv version

# 设置全局
jenv global oracle64-1.6.0.39

# 设置本地
jenv local oracle64-1.6.0.39

# 设置 shell
jenv shell oracle64-1.6.0.39 

# 移除
jenv remove oracle64-1.6.0.39
```

# 疑问

## 在使用 jenv 切换版本后 mvn -v 显示的 java 版本并不会改变，这是怎么回事呢？


```zsh
➜  .m2 mvn -v
Apache Maven 3.6.2 (40f52333136460af0dc0d7232c0dc0bcf0d9e117; 2019-08-27T23:06:16+08:00)
Maven home: /usr/local/Cellar/maven/3.6.2/libexec
Java version: 13.0.1, vendor: Oracle Corporation, runtime: /Library/Java/JavaVirtualMachines/jdk-13.0.1.jdk/Contents/Home
Default locale: en_CN, platform encoding: UTF-8
OS name: "mac os x", version: "10.15.1", arch: "x86_64", family: "mac"
➜  .m2 /usr/bin/java --version
java 13.0.1 2019-10-15
Java(TM) SE Runtime Environment (build 13.0.1+9)
Java HotSpot(TM) 64-Bit Server VM (build 13.0.1+9, mixed mode, sharing)
➜  .m2 java -version
java version "11.0.5" 2019-10-15 LTS
Java(TM) SE Runtime Environment 18.9 (build 11.0.5+10-LTS)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.5+10-LTS, mixed mode)
➜  .m2 which java
/Users/fang/.jenv/shims/java
➜  .m2
```

我猜，这个版本是和 `/usr/bin/java` 的版本一致。

这个真的不好验证，因为在 Mac 里即便是 root 用户，也没办法修改这个软连接和他指向的文件，但是 homebrew 却有权限，真是神奇。


  