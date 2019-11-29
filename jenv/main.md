# jenv

## Mac JDK 路径

```
/Library/Java/JavaVirtualMachines
```

安装Jdk: 直接从 Oracle 下载 Jdk 解压之后放到这个文件夹下面即可。

环境变量配置与切换：使用 jenv 。

## jenv 安装 

### brew

```bash
brew install jenv
```

### git clone

或者采用 git clone 从 github 上安装

[jenv.be](https://www.jenv.be/)

```bash
git clone https://github.com/gcuisinier/jenv.git ~/.jenv
```

### 配置

在 .zshrc 或者 .bash_profile 中加入一下内容完成配置

```
export PATH="$HOME/.jenv/bin:$PATH"
eval "$(jenv init -)"
```

## jenv 使用

```bash
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