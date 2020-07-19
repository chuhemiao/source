title: flutter 问题汇总
id: .nan
categories:
  - flutter
date: 2020-07-19 15:23:53
toc: true
tags: 
	- dart
  - ios
  - React native
  - flutter
keywords: 梦遥奇缘,ios,flutter,JS,typescript,react,YAF,禾子,js,http,安卓打包,ios打包,rn打包,des,3des
---


+ flutter doctor 一直卡住不动，可能是代理问题
    + export PUB_HOSTED_URL=https://pub.flutter-io.cn
    + export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn

macos/linux 设置中国镜像：   每次都要先执行一次 （export PATH="$PWD/flutter/bin:$PATH"）

1. export PUB_HOSTED_URL=https://pub.flutter-io.cn
2. export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
3. git clone -b dev https://github.com/flutter/flutter.git
4. export PATH="$PWD/flutter/bin:$PATH"
5. cd ./flutter
6. flutter doctor


然后运行flutter doctor -v 更新版本

flutter 环境之java环境，必须使用jdk8，否则会一直提示升级。


git clone 加速

git config --global http.https://github.com.proxy socks5://127.0.0.1:7891
或者打开 .gitconfig 文件，输入下面配置

[http "https://github.com"]
    proxy = socks5://127.0.0.1:1086
    

+ Waiting for another flutter command to release the startup lock...

    - 进入到你的flutter sdk目录中，然后找到bin/cache/lockfile文件，删除它即可。



CDN: trunk URL couldn't be downloaded:
      https://raw.githubusercontent.com
      


