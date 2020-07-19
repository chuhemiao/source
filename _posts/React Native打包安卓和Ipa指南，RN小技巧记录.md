title: React Native打包安卓和Ipa指南，RN小技巧记录
id: .nan
categories:
  - react
date: 2020-07-19 15:55:53
toc: true
tags: 
	- vscode
  - ios
  - React native
  - rn开发
keywords: 梦遥奇缘,ios,HTML,JS,typescript,react,YAF,禾子,js,http,安卓打包,ios打包,rn打包,des,3des
---


### CSS小技巧之文字实现竖排
+ 设置外层宽度，然后定位文字，给文字设置css行高（lineHeight应大于外层文字高度）
### IOS相关

+ `error Failed to build iOS project. We ran "xcodebuild" command but it exited with error code 65. To debug build logs further, consider building your app with Xcode.app, by opening cleaaan.xcworkspace`
+ 碰到code 65 可能和ios包管理有关，`cd ios && pod repo update && pod install && pod update`

+ ios键盘遮挡问题，使用APSL下组件：`[react-native-keyboard-aware-scrollview](https://github.com/APSL/react-native-keyboard-aware-scroll-view)` 

### JS相关
+ `TypeError: Invalid attempt to spread non-iterable instance`
+ 可能原因是数据和对象转换赋值导致不能遍历这个数据的问题，检查接口获取到之后的数据和当前state定义的数据之间互相赋值是否加了[...aaa],aaa为state定义的数组或对象，这里的...可能是导致错误出现的原因，去掉试试。


### React Native ios打包 IPA

+ `mkdir release_ios`

+ `npx react-native bundle --entry-file index.js --platform ios --dev false --bundle-output release_ios/main.jsbundle --assets-dest release_ios/`


+ `release_ios` 下的文件 添加到xcode项目，xx项目名 -》 add files to xxx项目 ->选择目录`release_ios-》folders`类型为`“Create folder references” -》 Add`


+ 添加证书、配置描述文件打包 -》·product ->archive => Distribute App· => 然后有4个选择，IOS App Store 上架、Development 测试，Enterprise 企业包，然后一直下一步，导出ipa

### React Native 安卓打包APK
+ 1.生成keystore
+ 2.设置 gradle 变量
+ 3.将签名配置加入到项目的 gradle 配置中
+ 4. `cd  android `
+ 5. `./gradlew assembleRelease`

+ keytool -genkeypair -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000

更多详细操作步骤推荐参考：

+ [React Native 官方打包APK](https://www.react-native.cn/docs/signed-apk-android)
+ [新版React Native发布APP之签名打包APK](https://www.devio.org/2019/11/08/react-native-Release-APP-Signature-Package-APK/)

+ Notice：Macos下可能需要sudo 
    - 执行 sudo ./gradlew assembleRelease

### 安卓打包线上realease版本安装后不能发起请求http问题

+ 安卓打包realease版本后，默认 ReactNative Android9.0以上打包apk后http无法请求

![AndroidManifest.xml](media/15944435878136/15951436861022.jpg)


+ 修改 `/当前项目名/android/app/src/main/AndroidManifest.xml`，增加配置在application中 `android:usesCleartextTraffic="true"`

### RN开发参考和React相关技术栈推荐

+ [React Native中文网](https://www.react-native.cn/)
+ [RN常用例子和demo](https://reactnativeexample.com/)
+ [React和RN技术、RN速查表，强烈推荐查看](https://shenbao.github.io/ishehui/index.html)
+ [Store、Redux、Reducer、action等数据相关知识，必学必看](https://cn.redux.js.org/)
+ [React 源码技术揭秘](https://react.iamkasong.com/)