title: 2020最新React Native 0.62.2版本开发指南总结
id: .nan
categories:
  - react
date: 2020-07-24 17:22:53
toc: true
tags: 
	- dart
  - ios
  - React native
  - flutter
keywords: 梦遥奇缘,ios,flutter,JS,typescript,react,YAF,redux,saga,http,安卓打包,ios打包,rn打包,des,3des
---


### 一个新手需要哪些基础知识上手RN开发？
+ 开发工具和插件等准备工作
+ Git基础
+ Javascript 基础
+ ES6 基础
+ CSS3 基础
+ Flex 布局
+ React 基础
+ Redux、Saga
+ React Native 基础
+ IOS开发者账号和Xcode使用基础
+ Android Studio使用和配置
+ API调试
+ 翻墙工具
+ 拓展学习

### 准备工作

+ 要想有一个效率的开发效果，必然需要一个效率的开发工具，因此开发工具和一些基础的插件已经成为开发者必备的工具，比如前端需要VSCode、WebStorm等，而后端则需要对应不同的语言使用不同的编辑器，比如Go用Goland、Java使用Idea、Php使用PhpStorm等。

+ 这里只介绍前端开发的一些基础工具，比如VSCode插件、Google Chrome插件。

+ 前端开发工具：
	- VS Code
	- WebStorm

+ 由于作者使用的是VS Code，所以也推荐此工具，简洁方便，外加强大的插件功能，让开发效率可以更高，当然玩法也变的更多。

![vscode 插件](https://i.loli.net/2020/07/24/KezFLDioVl7vBdW.png)

+ VS Code 需要哪些主题和基础的插件
	+ One Dark Pro ，主题，根据自己喜欢选择即可
	+ vscode-leetcode，刷题必备神器
	+ Path Intellisense，自动补全路径，在也不用一直输入
	+ Document this，js快速注释模版
	+ Beautify ，代码格式化
	+ React Native Tools，调试、提示
	+ ESLint ，语法检查
	+ vetur，vue语法高亮
	+ Atuo Rename Tag 、Auto Close Tag，自动补全Tag标签，修改时同步，补全闭合标签
	+ Git History，图形化查看git历史提交
	+ JavaScript (ES6) code snippets，es6语法提示高亮
	+ ES7 React/Redux/GraphQL/React-Native snippets，R系列开发必备

+ 谷歌Chrome 插件
	+ FeHelper，json格式化、网页取色、时间戳等常用工具
	+ Adblock Plus、ublock，屏蔽广告必备
	+ Momentum ,简洁的新标签页
	+ React Developer Tools ， react调试工具
	+ Vue.js devtools ，vue调试工具
	+ Quick QR ， 二维码生成器
	+ 划词翻译
	+ postman，调试接口必备
	+ wappalyzer ， 查看网页使用的技术

### Git基础

+ git是什么？
	+ 是一个分布式版本控制软件。
+ [git知识大全指南](https://git-scm.com/book/zh/v2/)
+ [git基础指南](https://rogerdudler.github.io/git-guide/index.zh.html)
+ [廖雪峰,Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)
+ [猴子都能懂的Git基础，进阶](https://backlog.com/git-tutorial/cn/intro/intro1_1.html)

### Javascript 基础

+ 推荐使用 MDN JS入门教程
	+ [JavaScript基础](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics)

### ES6 基础

+ 什么是ES6？
	+ ECMAScript 6.0（以下简称ES6）是JavaScript语言的下一代标准，已经在2015年6月正式发布了。它的目标，是使得JavaScript语言可以用来编写复杂的大型应用程序，成为企业级开发语言。

+ 入门文档推荐
	+ [阮一峰 ES6 入门教程](https://es6.ruanyifeng.com/)
	+ [ES6 入门文档](http://caibaojian.com/es6/)

### CSS3 基础

+ Css做为页面的重要属性和Html，Js一样，建议先了解Css，然后在学习Css3如何布局、盒子模型、样式层叠等其他属性。
+ [MDN Css 入门介绍](https://developer.mozilla.org/zh-CN/docs/Web/CSS)
+ [CSS3开发文档](https://segmentfault.com/a/1190000018585523)
+ [Css/Css3样式参考手册](http://css.cuishifeng.cn/)

### Flex 布局

+ 什么是flex布局？
	+ Flexible Box 模型，通常被称为 flexbox，是一种一维的布局模型。它给 flexbox 的子元素之间提供了强大的空间分布和对齐能力。
	+ 使用Flex布局很大程度上是为了适配不同机型，甚至是这种形式的布局更有效率去开发项目，节省时间。
	+ [MDN Flex布局基础知识](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)

+ flex布局教程指南
	+ [阮一峰 Flex 布局教程：语法篇](https://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
	+ [阮一峰 Flex 布局教程：实例篇](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)

+ Css3 Flexbox布局口诀
	+ [5张图看懂Flexbox布局](https://weibo.com/1712131295/CoRnElNkZ?ref=collection&type=comment#_rnd1595575656531)

+ 延伸阅读
	+ [深度解析 CSS Flexbox 布局](https://juejin.im/post/5e8ae27df265da47f144a8db)

### React 、Redux 基础

+ React 基础
	+ 学习是一个循序渐进的过程，推荐先看官方的基础文档，并上手直接写代码，跟着demo走起来，看再多说在多，不如直接做，逼逼那么多根本没用，不是天才就努力实干。对于大多数语言而言，目前大多数官方教程足够让你学会基础，如果不能让新手上手（没有笨的学生，只有教不好的老师），那只能说这是一门失败的语言... 
	+ [官方文档入门学习React](https://zh-hans.reactjs.org/tutorial/tutorial.html)

+ 拓展使用第三方教程
	+ 全栈公开课，Part 1 部分讲解React入门，当然也推荐从头开始，系统的学习Web开发，也可以直接学习React和Redux部分
	+ [FullStack--React和Redux基础](https://fullstackopen.com/zh#course-contents)
	+ [React 教程--菜鸟教程版](https://www.runoob.com/react/react-tutorial.html)
	+ [快速入门React基础知识](https://shenbao.github.io/ishehui/html/React/React%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html)

+ Redux、Store、Saga、Reducer基础
	+ 数据管理是APP开发的一大难题，因此有很多解决方案供大家使用，比如Redux、Saga、Dva这些，当然也有一些先进的，比如Rematch，或是一些高阶函数、Promise方式，后者是群里听大佬们谈论的，目前还没有实践，不过看了hook这些方式，确实用起来都会省事不少。
	+ [Redux、Store、Reducer文档](https://cn.redux.js.org/)
	+ [Redux-Saga文档和用法](https://redux-saga-in-chinese.js.org/)

+ 拓展使用替代Redux方案，Rematch
	+ Rematch是 在 Redux 的基础上构建并减少了样板代码和执行了一些最佳实践，使用rematch可以不用写一堆types、action、store、saga等，写完项目交流的时候发现的，目前我们项目用的还是老一套Redux、Saga、Reducer，写起来type、saga，state等状态是真的痛苦，或许Rematch是更好的选择。
	+ [Rematch官方文档](https://rematch.gitbook.io/handbook/)

### React Native 基础

+ 有了以上基础，写基础的页面应该不是啥大问题，而对于RN开发，则需要学习对应的文档，了解一些基础的UI组件使用、组件复用、网络请求、flexbox布局、数据存储（AsyncStorage）、loading加载、手机适配、与原生IOS、安卓交互等。

+ 往远了说，在一切页面布局开始写的时候，同时应该规划好接口的调用和字段、mock数据格式、数据的持久化、打包的方式、热更新等。

+ RN基础之环境安装
	+ RN中文网，入门就是教你如何搭建环境，有win版和macos版，基本按着流程走不会出太大的问题，都可以跑起来初始化的项目。
	+ [React Native开发环境搭建指南](https://www.react-native.cn/docs/getting-started)
	+ 此处可能遇到的问题，如果是iOS，则可能出现CocoaPods版本问题、超时问题、选择master版本问题、更多问题可以看[issues](https://github.com/CocoaPods/CocoaPods/issues),brew 比较慢的问题，基本都是网的问题，推荐使用清华源，[brew update无反应](https://www.jianshu.com/p/62f1b963baa6),或者直接上代理，并设置git的拉取方式，设置socks5代理端口，此方式同理适用npm、git clone,[如何设置git socks5端口](https://gist.github.com/laispace/666dd7b27e9116faece6)。
	+ 如果是安装安卓版本，则可能遇到sdk版本问题，java jdk需要1.8（java8）版本，然后安装Android Studio 需翻墙，否则网站都进不去.安卓环境90%都是网络问题，这里翻墙情况下推荐使用电信网络，移动可能卡住不动。
	+ [推荐一个稳定的机场,speed](https://speedsss.com/auth/register?ref=kP782G)

+ 组件化和组件复用
	+ RN和Flutter差不多，都是一切组件化，因此在开发的时候，则需要组件化，最终拼接一切完成设计稿里的页面样式，组件复用会很大程度上减少耦合，加快开发进度，减少工作时间，规划好组件复用会事半功倍。
	+ 一般情况下：列表、交互、loading、toast会复用的比较多，比如一些Button、列表渲染、line、layout、layoutscroll、TouchableOpacity交互等一些常用的组件，应该让他们独立出来复用。

+ 数据请求和数据持久化
	+ http请求一般使用axios，封装post、get，请求头等参数，根据不同需求使用即可
	+ 数据持久化，推荐使用AsyncStorage+reducer，可以安卓、ios同时适配，也是官方的包。

+ RN 路由、Bottom 
	+ 推荐使用[React Navigation](https://reactnavigation.org/docs/getting-started)，功能全，生态完善，版本在持续升级，不过坑的是可能新旧版本语法不一样。
	+ 备选：[Wix React Navigation](https://wix.github.io/react-native-navigation/docs/before-you-start),有基础的功能，不过功能不如React Navigation 功能强大，相对的github也不如React Navigation活跃度高。

### IOS开发者账号和Xcode使用基础

+ [Xcode打包IOS之证书签名配置](https://www.jianshu.com/p/083c72de47b0) 

+ [iOS 打包发布最新流程](https://www.devio.org/2020/03/15/React-Native-releases-packaged-iOS-apps-for-apps/)
+ 注意事项，一般情况下不要升级Xcode，否则会导致项目跑不起来，同理安卓AS也一样，IOS开发者账号可能会遇到签名问题、添加测试机设备、打包AD hoc包等问题。
+ 一般情况下添加新的udid之后需要重新配置Profiles,选择已经添加的设备之后，一直下一步，最后通过Xcode导入当前下载的证书，然后重新打包hoc包即可。
+ Xcode 模拟器或真机调试时需要开启:`automatically manage signing`,并选择开发者账号和已经配置的Profiles，然后设置Build Settings 搜索sign，设置debug和release的四个选项为`Apple Development`,重新打包启动即可。
+ 更多ios开发遇到的问题，请查看同时间发布的其他文章，或者加[TG](https://t.me/kkdelos)咨询我。

### Android Studio使用和配置

+ 安卓环境基本按照官方文档都可以顺利完成，并跑起来，而更多的坑则是后期开发中需要设置xml配置，gradle配置，引用第三方包需要增加配置等问题。
+ 关于安卓开发中遇到的问题，请查看:"RN小技巧记录系列文章"。

### API调试

+ 接口调试也是前端必备技能，毕竟数据不能只使用假的，而对于调试接口，则需要看后端如何提供稳定，比如java、go、php都有swag在线调试，而对于没有swag的则可以使用postman发请求看接口的情况，当然你也可以直接使用axios去调试。
+ 在高端一点，可以使用抓包工具`Charles、Fiddler`等抓包工具查看返回情况和请求情况。



### 翻墙工具

+ 万恶的GFW，真是难为了国内的广大开发者。
+ 推荐使用，有钱可以直接上Surge，要不就选V2ray、Trojan模式
+ 客户端推荐使用：[ClashX](https://github.com/yichengchen/clashX/releases)、Shadowrocket、Quantumult X、[V2RayX](https://github.com/Cenmrev/V2RayX/releases)
+ 科学上网的方式
	+ 自建：推荐使用Vultr，[快速注册Vultr获取100美元测试金](https://www.vultr.com/?ref=8557913-6G)
+ 机场千万家如何选？
	+ 不想折腾就买稳定的，否则就白嫖吧，反正不花钱,网上有很多分享ss的不过不是很安全。
	+ [注册白嫖版，邀请码过期请评论区留言](https://speed17.com/#/register?code=llNeSueq)
	+ [注册便宜版V2ray](https://v2.qovoq.ml/#/register?code=EWAnpomv)
	+ [注册稳定付费版V2ray，支持Clashx](https://speedsss.com/auth/register?ref=kP782G)

### 拓展学习

+ [Typescript基础入门](https://fullstackopen.com/zh/part9)
+ [开课吧web全栈架构师第4期](https://pan.baidu.com/s/1flEC_MvIYXAVDo94WesCSw), 提取码: az94
+ [seo魔贝8期](https://pan.baidu.com/s/19XDotXphjuViwJzJFiW5Rg), 提取码: qnua

### RN相关博客推荐

+ [贾鹏辉的技术博客，RN开发部分](https://www.devio.org/tags/#React%20Native)
+ [trello上的RN指南和讨论](https://trello.com/b/Lbq1o6L9/learning-react-native)
+ [RN的一些组件和demo事例](https://reactnativeexample.com/)
+ [React和React Native组件库](https://react.parts/)
+ [React技术揭秘](https://react.iamkasong.com/#)

