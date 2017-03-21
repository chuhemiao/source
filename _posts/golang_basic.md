title: GO基础安装
id: .nan
categories:
  - GO
date: 2017-03-21 18:03:53
toc: true
tags: 
	- golang
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

##  linux下安装go的步骤


+ [GO下载地址](https://golang.org/dl/)
+ `wget   https://storage.googleapis.com/golang/go1.7.4.linux-amd64.tar.gz`
+ `tar -C /usr/local/ -xzf go1.7.4.linux-amd64.tar.gz`
+ #在/etc/profile添加变量
	- `vi /etc/profile`
	- #go 环境变量
	- `export GOROOT=/usr/local/go/bin`
	- `export GOPATH=$PATH:$GOROOT/bin`
	- `source /etc/profile`

+ 测试当前版本 `go version`
+ 构建GO  `/usr/local/go/src`   `./all.bash`

## NOTICE

+ 如果当前没有安装之前版本(go1.6)，需要先安装低版本才能继续安装高版本




