title: 解决CFBundleIdentifier", Does Not Exist
id: .nan
categories:
  - react
date: 2017-10-29 21:59:08
tags: git
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
description: 有时候的失去未必不是一件好事，只是人生中的过客，又何必在意那么多。失去了才会懂得珍惜吗？
---

# mac 下运行react-native run-ios 报错 CFBundleIdentifier", Does Not Exist

1.产生原因：/Users/你的用户名`/.rncache中boost_1_63_0.tar.gz，double-conversion-1.1.5.tar.gz，folly-2016.09.26.00.tar.gz，glog-0.3.4.tar.gz文件不完整。或者node_modules/react-native/third-party` 文件不完整。
+ 删除/user/你的用户名/.rncache目录下的`boost_1_63_0`，重新下载安装
+ 打开命令行工具，在项目目录下输入`rm -rf node_modules && rm -rf ~/.rncache && yarn`
+ `npm install`  
+ `react-native upgrade` 
+ 运行 `react-native run-ios`

2. [github解答](https://github.com/facebook/react-native/issues/7308) ，似乎大多数点赞的是路径问题，配置真是一大难题！

3. 如果以上问题仍然不能解决，那么你可以重新删除，编译环境生成项目，然后使用梯子代理全局模式下`npm install`（或者使用yarn），全局模式下最新版`react-native`并未出现 `CFBundleIdentifier`问题。

