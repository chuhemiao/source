title: H5如何实时在手机上调试页面并抓包
id: .nan
categories:
  - javascript
date: 2020-08-14 17:28:53
toc: true
tags: 
	- chrome
    - cookie
    - spyDebugger
    - webview
keywords: 梦遥奇缘,ios,HTTPOnly,JS,typescript,react,SameSite,js,前端开发,安卓打包,ios打包,谷歌浏览器,des,3des
---


### 调试方法

+ 使用safari自带调试，需连接数据线，chrome同理，更多详情请查看：[Safari和Chrome浏览器真机调试](https://juejin.im/post/6844903977557950471)
+ 方式二，使用spy-debugger调试

### 调试工具

[spy-debugger](https://github.com/wuchangming/spy-debugger) 用来调试安卓、IOS 、webview 等 H5页面适配问题，抓包的话主要用在webview，调试页面适配spy-debugger还是很方便的，不需要连接数据线，直接可以访问多人同时调试。


### 使用说明

+ 安装：
	+ win 下=》 `npm install spy-debugger -g`
	+ macOS 下=〉 `sudo npm install spy-debugger -g`

+ 启动
	+ 命令行输入：`spy-debugger`
	+ ![启动spy debugger](https://i.loli.net/2020/08/10/bZujnayV2oNHwmM.png)

+ 上手调试必备条件
	+ 手机和电脑在同一wifi下
	+ 命令行输入：`spy-debugger` win或macOS下如果启动不了命令，请关闭防火墙后重试
	+ 设置当前手机http代理，如上图打开的端口，默认是9888，然后是自己当前本机的ip地址
		+ Android设置代理步骤：设置 - WLAN - 长按选中网络 - 修改网络 - 高级 - 代理设置 - 手动
		+ iOS设置代理步骤：设置 - 无线局域网 - 选中网络 - HTTP代理手动

### ios需要单独安装证书
+ Safari访问地址 [cert 安装](http://spydebugger.com/cert) ，允许，安装，输入密码，完成即可


### 如何访问

+ 设置好端口后，手机浏览器输入`spy-debugger`启动时的ip和本地启动项目的端口
+ 比如：当前启动的ip是：192.168.2.36，本地启动的项目访问地址是：`http://localhost:8080`，即得出调试地址为：`http://192.168.2.36:8080`

### 抓包

![spy-debugger抓包](https://i.loli.net/2020/08/10/8hOx7LX2GA4TBlH.png)

如上图所示，当前的method，host，即为调试起发起的请求，点击对应的请求可以看到Response返回内容

### 自定义设置端口、代理

+ 启动指定端口：spy-debugger -p 8888
+ 设置代理：spy-debugger -e http://127.0.0.1:7980
+ 更多自定义配置请查看[文档说明](https://github.com/wuchangming/spy-debugger)


