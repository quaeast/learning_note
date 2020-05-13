# Go

## 环境变量

### GOPATH, GOROOT，GOBIN

官方文档

>The install directory is controlled by the GOPATH and GOBIN environment variables. If GOBIN is set, binaries are installed to that directory. If GOPATH is set, binaries are installed to the bin subdirectory of the first directory in the GOPATH list. Otherwise, binaries are installed to the bin subdirectory of the default GOPATH ($HOME/go or %USERPROFILE%\go).

Jetbrains 

>GOROOT is a variable that defines where your Go SDK is located. You do not need to change this variable, unless you plan to use different Go versions.

>GOPATH is a variable that defines the root of your workspace. By default, the workspace directory is a directory that is named go within your user home directory (~/go for Linux and MacOS, %USERPROFILE%/go for Windows). GOPATH stores your code base and all the files that are necessary for your development. You can use another directory as your workspace by configuring GOPATH for different scopes. GOPATH is the root of your workspace and contains the following folders:
>
>* src/: location of Go source code (for example, .go, .c, .g, .s).
>* pkg/: location of compiled package code (for example, .a).
>* bin/: location of compiled executable programs built by Go.

* GOROOT：指定 go sdk
* GOPATH: 指定 workspace
* GOBIN: 等价于 GOPATH/bin

## 命令

```sh
# 就地编译
go build -o hello hello.go


```

