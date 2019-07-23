title: Go 语言解决不能Go get安装Gin问题解决方案
id: .nan
categories:
  - GO
date: 2019-07-23 17:03:53
toc: true
tags: 
	- golang
    - gin
    - echo 
    - goproxy
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

### 1.问题描述

```
Go get 出现超时问题：“golang unrecognized import path "golang.org/x/net   unrecognized import path "golang.org/x/sys"  Unknown SSL protocol error in connection to gopkg.in:443 "”
```

### 2.解决办法

+ 网络上解决方案1手动下载：
```
mkdir $GOPATH/src/golang.org/x
cd $GOPATH/src/golang.org/x
git clone git@github.com:golang/text.git
```

### 方案二：设置代理

```
export http_proxy=https://proxyAddress:port
export https_proxy=https://proxyAddress:port
```

### 3.最佳解决方案

+ 从 Go 1.11 版本开始已经开始支持Go Mod ，并且提供了包下载的解决方案，就是使用 https://goproxy.io/ 直接代理下载，官方设置方法：

+ macos/linux  

```
export GO111MODULE=on 
export GOPROXY=https://goproxy.io
```

+ Wins 使用PowerShell 设置（这里输入是去当前设置的GOPATH）

```
$env:GO111MODULE="on"
$env:GOPROXY="https://goproxy.io"
```

![go-gin-golang](https://cdn.bsatoshi.com/2019/07/23/72B1D829-1628-4CC9-8129-053951E159C2.png)

+ 提示这里需要加入引号，否则会报on或地址有问题，之后在执行Go get 等其他命令都一帆风顺了。

### Notice： 如果你使用的Go version 》=1.13  请使用

```
go env -w GOPROXY=https://goproxy.io,direct
go env -w GOPRIVATE=*.corp.example.com
```


Go 成功安装Gin框架并使用Go mod管理

![安装Gin框架并使用Go](https://cdn.bsatoshi.com/2019/07/23/1C3E1CAC-D142-49F0-95C8-5243B1EB701C.png)

参考资料：
https://goproxy.io/
[一键解决 go get golang.org/x 包失败](https://segmentfault.com/a/1190000018264719)
