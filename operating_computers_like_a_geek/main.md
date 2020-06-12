# Operating Computers Like a Geek

> 深入理解计算机系统，并熟练操作是所有计算机工作的基础。一个月速成，像极客一样操作计算机。

* 安装相关图形软件
* shell/UNIX 基本使用 / git 基本使用
* Python
* git 基本使用
* Django

本文默认 Linux 是一种特殊的 Unix，所以通用部分使用 Unix，特殊部分强调 Linux。

## 安装相关图形软件

### （Windows）从 app store 安装 windows terminal、ubuntu

[wsl tutorial](https://docs.microsoft.com/zh-cn/windows/wsl/install-win10)

[windows 内核升级助手](https://www.microsoft.com/zh-cn/software-download/windows10ISO)

安装windows terminal 可能需要升级内核版本。

不必要安装wsl2，运行链接1中第一条命令即可重启

### （Mac）从 app store 安装 xcode，之后安装 xcode command tools

[Xcode-command-tools download](https://developer.apple.com/xcode/resources/)

### 安装 vscode

[vscode download](https://code.visualstudio.com/)

### 安装 typora

[typora download](https://www.typora.io/)

* 图形界面软件安装
* 学会使用 Markdown 记笔记

## shell / Unix 基本使用 / git 基本使用

### 安装 git

[git download](https://git-scm.com/downloads)

[apt commands](https://quaeast.cn/apt/main.html)

* 学会使用包管理软件 brew/apt/yum

### 注册GitHub

[github.com](https://github.com/)

### 配置ssh-key，连接远程服务器（github）

[ssh toturial](https://quaeast.cn/ssh/main.html)

[简明 VIM 练级攻略](https://coolshell.cn/articles/5426.html)

* 理解非对称加密
* 学会使用命令行软件，理解参数，变量，常量
* vim 基本使用
* 理解 Unix 系统文件权限（秘钥权限）

### 安装 zsh/oh-my-zsh

[install zsh](https://ohmyz.sh/)

* 理解什么是 shell
* 理解 Unix 目录结构
* 理解环境变量和 .bashrc/.zshrc
* 理解一切皆文件
* 理解 Linux 用户和权限控制


### 实践：购买阿里云 Linux 服务器，并搭建自己的vpn

[aliyu](https://www.aliyun.com/?utm_content=se_1000301881)

[ipsec setup](https://github.com/hwdsl2/setup-ipsec-vpn)

* 学会使用 ssh 连接服务器

## Python 

### 安装 Anaconda

[anaconda download](https://www.anaconda.com/)

* 配置 .zshrc/.bashrc，复习环境变量的概念
* conda 环境管理
* 理解 Python 包管理
* 理解 Python 本质上也是一种 shell

### 基础 Python 语法

[python torurial](https://www.liaoxuefeng.com/wiki/1016959663602400)

* 变量（深刻理解类型）
* 流程控制（分支，循环）
* 函数
* 类

## Git 基本使用

### 下载 desktop 客户端

[github desktop download](https://desktop.github.com/)

* 学会创建 Git 项目，上传到 GitHub
* 学会使用基本的 git 命令

### 实践：将之前的笔记上传到 GitHub

[git 功能](https://quaeast.cn/git_function_oriented/main.html)

* 使用 GitHub desktop
* 创建 GitHub 项目

### 使用 vuepress 搭建个人博客

https://vuepress.vuejs.org/guide/#how-it-works

### 使用 nginx 建立静态网站

https://quaeast.cn/nginx_http/main.html

### 购买域名和 ssl 证书，配置 DNS 和 CDN

https://www.cloudflare.com/

* 理解静态网站
* 初步理解 http

## Django 

https://docs.djangoproject.com/en/3.0/intro/tutorial01/

* 开发简易的 web 应用
* 阅读文档
* 语言运用
* 理解 web
* 继续理解 http

### 实践：按照 tutorial 搭建 polls