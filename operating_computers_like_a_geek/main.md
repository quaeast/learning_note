# Operating Computers Like a Geek

![Feynman](./img/Feynman.png)

> 核心内容：在 shell 层理解 Unix ，实践静态和动态 web，入门 B/S 架构。

* 安装相关图形软件
* shell / UNIX 基本使用，git 基本使用
* Python
* 搭建静态网站：VuePress
* 搭建动态网站：Django

本文默认 Linux 是一种特殊的 Unix，所以通用部分使用 Unix，特殊部分强调 Linux。

## 安装相关图形软件

### （Windows）从 app store 安装 windows terminal、ubuntu

[wsl tutorial](https://docs.microsoft.com/zh-cn/windows/wsl/install-win10)

[windows 内核升级助手](https://www.microsoft.com/zh-cn/software-download/windows10ISO)

安装 windows terminal 可能需要升级内核版本。

不必要安装 wsl2，运行链接 1 中第一条命令即可重启

### （Mac）从 app store 安装 xcode，之后安装 xcode command tools

[Xcode-command-tools download](https://developer.apple.com/xcode/resources/)

### 安装 vscode

[vscode download](https://code.visualstudio.com/)

### 安装 typora

[typora download](https://www.typora.io/)

* 图形界面软件安装
* 学会使用 Markdown 记笔记

## shell / Unix 基本使用，git 基本使用

### 安装 zsh/oh-my-zsh

[install zsh](https://ohmyz.sh/)

* 理解什么是 shell
* 理解 Unix 目录结构
* 理解环境变量和 .bashrc/.zshrc
* 理解一切皆文件
* 理解 Linux 用户和权限控制

### 安装 git

[git download](https://git-scm.com/downloads)

[apt commands](https://quaeast.cn/apt/main.html)

* 学会使用包管理软件 brew/apt/yum

### 注册GitHub

[github.com](https://github.com/)

[Github Desktop](https://desktop.github.com/)

* 安装 GitHub Desktop

### 配置ssh-key，连接远程服务器（github）

[ssh tutorial](https://quaeast.cn/ssh/main.html)

[简明 VIM 练级攻略](https://coolshell.cn/articles/5426.html)

* 理解非对称加密
* 学会使用命令行软件，理解参数，变量，常量
* vim 基本使用
* 理解 Unix 系统文件权限（秘钥权限）

### 实践：将之前的笔记用 git repo 保管，并上传到 github

[Reference Manual](https://git-scm.com/docs)

[Pro Git book](https://git-scm.com/book/en/)

[极客时间 git 视频教程（完整版我买过，可以管我要）](https://www.bilibili.com/video/BV1mJ411X7E8?from=search&seid=11155582492233674745)

[我的 git 笔记（比较繁琐）](https://quaeast.cn/git/main.html#%E4%B8%AA%E4%BA%BA%E5%B7%A5%E4%BD%9C)

[git 功能](https://quaeast.cn/git_function_oriented/main.html)

git 作为版本控制工具，也是非常重要团队协作工具。操作好 git 是技术人员的底线。推荐观看视频教程了解基本操作，深入了解可阅读《Pro Git》，权威参考见官方文档。

个人操作需掌握如下子命令：

* git init
* git add
* git commit
* git status
* git log
* git checkout
* git reset
* git push
* git fetch/rebase/merge

### 实践：购买阿里云 Linux 服务器，并搭建自己的vpn

[aliyun](https://www.aliyun.com/?utm_content=se_1000301881)

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

## 搭建静态网站：VuePress

### 使用 vuepress 搭建个人博客

[vuepress tutorial](https://vuepress.vuejs.org/guide/#how-it-works)

[YAML 语言教程](http://www.ruanyifeng.com/blog/2016/07/yaml.html)

[Linux 用户管理](https://quaeast.cn/linux_user_management/main.html)

* 尝试阅读技术文档
* 实践 Linux 用户管理
* Linux 手动安装 node（复习目录结构、环境变量、文件概念……）
* 理解 node，学会使用 npm
* 理解 json/yml 等配置文件格式

### 使用 nginx 建立静态网站

[nginx 建立静态网站](https://quaeast.cn/nginx_http/main.html)

* 理解静态网站
* 理解服务器
* 初步理解 http

### 购买域名和 ssl 证书，配置 DNS 和 CDN

[cloud flare](https://www.cloudflare.com/)

* 尝试阅读技术文档
* 初步理解 https，复习非对称加密

## 搭建动态网站：Django

### 实践：按照 tutorial 搭建 polls

[Django tutorial](https://docs.djangoproject.com/en/3.0/intro/tutorial01/)

[MVC，MVP 和 MVVM 的图示](http://www.ruanyifeng.com/blog/2015/02/mvcmvp_mvvm.html)

模板语言（后端渲染页面）技术已经不是当前主流，目前的单网页应用都是采用 REST/Ajax 等技术进行前后端分离开发。这个实践的目的是理解动态网站和 MVC 模式。

Python/Golang 是当前微服务模式的主流开发语言，RESTful API 的开发其实大同小异。

* 开发简易的 web 应用
* python 语言运用
* 理解 web
* 进一步理解 http
* 理解 MVC 模式
* 理解服务器渲染和前端渲染的区别

## 完结

本教程偏向动手，没有涉及计算机科学的压箱底绝活：数据结构，算法，编译等。目标是理解计算机系统、培养动手能力和阅读文档的能力。