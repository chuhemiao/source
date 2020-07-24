title: React native 遇到的bug记录和解决方式
id: .nan
categories:
  - react
date: 2020-06-24 18:03:53
toc: true
tags: 
	- dart
  - ios
  - React native
  - flutter
keywords: 梦遥奇缘,ios,flutter,JS,typescript,react,reactnative,js,http,安卓打包,ios打包,rn打包,des,3des
---

###  小米手机无法通过 `adb install 或sudo npx react-native run-android` 安装apk包

 + 首先确保自己开启了端口 `adb reverse tcp:8081 tcp:8081` ,然后运行`sudo npx react-native run-android` 然后出现错误： `Failure [INSTALL_FAILED_USER_RESTRICTED: Install canceled by user]`
 + 解决：小米（mi8青春版）手机安装测试包需要允许手机使用USB安装应用，只打开开发者和连接USB是没有用的，能用的功能是充电，因此需要在手机上设置-》更多设置-〉开发者选项-》打开USB安装；
 + 然后在运行adb install 安装apk或者直接使用`sudo npx react-native run-android`安装

### Oppo部分机型出现不能使用相机和存储功能

`Android APIv29 FileNotFoundException EACCES (Permission denied)`

修改application 配置：`android:requestLegacyExternalStorage="true"`

### IOS请求正常，安卓机小米、oppo部分机型不能使用axios请求，一直出现Network error  (Android)

+ RN 版本：0.62.2
+ axios ：0.19.2
+ 修改安卓下配置：`android > gradle.properties` => `FLIPPER_VERSION=0.39.0 `

### 安卓部分机型出现打开debug不能点击屏幕

+ 打开debug时需要不能切换屏幕，并把当前debug在窗口最前面，使用终端调试即可（需要双屏幕，否则不能玩）