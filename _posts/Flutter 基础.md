title: Flutter 基础
id: .nan
categories:
  - flutter
date: 2020-05-29 23:58:53
toc: true
tags: 
	- dart
  - eth
  - React native
  - Truffle
  - dapps
keywords: 梦遥奇缘,ios,flutter,JS,typescript,react,YAF,禾子,js,http,安卓打包,ios打包,rn打包,des,3des
---


### Stateful widget 和Stateless widget

+ 有状态的组件（Stateful widget） 和无状态的组件（Stateless widget）有两点不同：
    + Stateful widget可以拥有状态，这些状态在widget生命周期中是可以变的，而Stateless widget是不可变的。
    + Stateful widget至少由两个类组成：
        - 一个StatefulWidget类。
        - 一个 State类； StatefulWidget类本身是不变的，但是State类中持有的状态在widget生命周期中可能会发生变化。

### Navigator，MaterialPageRoute=》路由管理

+ 路由(Route)在移动开发中通常指页面（Page），这跟web开发中单页应用的Route概念意义是相同的，Route在Android中通常指一个Activity，在iOS中指一个ViewController。所谓路由管理，就是管理页面之间如何跳转，通常也可被称为导航管理。

+ 导航管理都会维护一个路由栈，路由入栈(push)操作对应打开一个新页面，路由出栈(pop)操作对应页面关闭操作，而路由管理主要是指如何来管理路由栈。

// 路由跳转例子，调用Navigator.push方法，return到一个新的路由页面（NewRoute）

onPressed: () {
  //导航到新路由   
  Navigator.push( context,
   MaterialPageRoute(builder: (context) {
      return NewRoute();
   }));
},

+ 路由之=》MaterialPageRoute
    - MaterialPageRoute继承自PageRoute类，PageRoute类是一个抽象类，表示占有整个屏幕空间的一个模态路由页面，它还定义了路由构建及切换时过渡动画的相关接口及属性。MaterialPageRoute 是Material组件库提供的组件，它可以针对不同平台，实现与平台页面切换动画风格一致的路由切换动画：

    - 对于Android，当打开新页面时，新的页面会从屏幕底部滑动到屏幕顶部；当关闭页面时，当前页面会从屏幕顶部滑动到屏幕底部后消失，同时上一个页面会显示到屏幕上。
    - 对于iOS，当打开页面时，新的页面会从屏幕右侧边缘一致滑动到屏幕左边，直到新页面全部显示到屏幕上，而上一个页面则会从当前屏幕滑动到屏幕左侧而消失；当关闭页面时，正好相反，当前页面会从屏幕右侧滑出，同时上一个页面会从屏幕左侧滑入。

+ MaterialPageRoute使用参数介绍

MaterialPageRoute({
    WidgetBuilder builder,
    RouteSettings settings,
    bool maintainState = true,
    bool fullscreenDialog = false,
})

builder 是一个WidgetBuilder类型的回调函数，它的作用是构建路由页面的具体内容，返回值是一个widget。我们通常要实现此回调，返回新路由的实例。

settings 包含路由的配置信息，如路由名称、是否初始路由（首页）。

maintainState：默认情况下，当入栈一个新路由时，原来的路由仍然会被保存在内存中，如果想在路由没用的时候释放其所占用的所有资源，可以设置maintainState为false。

fullscreenDialog表示新的路由页面是否是一个全屏的模态对话框，在iOS中，如果
fullscreenDialog为true，新页面将会从屏幕底部滑入（而不是水平方向）。

+ 路由之Navigator
    - Navigator是一个路由管理的组件，它提供了打开和退出路由页方法。Navigator通过一个栈来管理活动路由集合。通常当前屏幕显示的页面就是栈顶的路由。Navigator提供了一系列方法来管理路由栈，在此我们只介绍其最常用的两个方法：
        +  Future push(BuildContext context, Route route)
        +  将给定的路由入栈（即打开新的页面），返回值是一个Future对象，用以接收新路由出栈（即关闭）时的返回数据。
        +  bool pop(BuildContext context, [ result ])
        +  将栈顶路由出栈，result为页面关闭时返回给上一个页面的数据。

+ 判断用户是否登陆，onGenerateRoute属性
    - 它在打开命名路由时可能会被调用，之所以说可能，是因为当调用Navigator.pushNamed(...)打开命名路由时，如果指定的路由名在路由表中已注册，则会调用路由表中的builder函数来生成路由组件；如果路由表中没有注册，才会调用onGenerateRoute来生成路由。
    - 全局的路由跳转前置处理逻辑。

### pubspec之 包管理

+ flutter如何使用配置文件pubspec.yaml（位于项目根目录）来管理第三方依赖包。

+ YAML是一种直观、可读性高并且容易被人类阅读的文件格式，它和xml或Json相比，它语法简单并非常容易解析，所以YAML常用于配置文件，Flutter也是用yaml文件作为其配置文件。
+ yaml例子和参数说明：
    - name：应用或包名称。
    - description: 应用或包的描述、简介。
    - version：应用或包的版本号。
    - dependencies：应用或包依赖的其它包或插件。
    - dev_dependencies：开发环境依赖的工具包（而不是flutter应用本身依赖的包）。
    - flutter：flutter相关的配置选项。
+ dependencies和dev_dependencies的区别，前者的依赖包将作为APP的源码的一部分参与编译，生成最终的安装包。而后者的依赖包只是作为开发阶段的一些工具包，主要是用于帮助我们提高开发、测试效率，比如flutter的自动化测试包等

name: flutter_in_action
description: First Flutter application.

version: 1.0.0+1

dependencies:
  flutter:
    sdk: flutter
  cupertino_icons: ^0.1.2
  // 新添加的依赖
  english_words: ^3.1.3
dev_dependencies:
  flutter_test:
    sdk: flutter

flutter:
  uses-material-design: true

+ 如何使用新包：直接将所依赖的包添加到dependencies下，然后运行：flutter packages get
### pubspec 之资源管理
+ assets指定应包含在应用程序中的文件， 每个asset都通过相对于pubspec.yaml文件所在的文件系统路径来标识自身的路径。asset的声明顺序是无关紧要的，asset的实际目录可以是任意文件夹（在本示例中是assets文件夹）。
+ flutter:
  assets:
    - images/my_icon.png
    - images/background.png

+ 加载当前在pubspec设置的assets图路径,两种方法都可以

Image(
  image: AssetImage("images/my_icon.png"),
  width: 100.0
);

Image.asset("images/avatar.png",
  width: 100.0,
)

+ 加载网络图片：

Image(
  image: NetworkImage(
      "https://avatars2.githubusercontent.com/u/20411648?s=460&v=4"),
  width: 100.0,
)

Image.network(
  "https://avatars2.githubusercontent.com/u/20411648?s=460&v=4",
  width: 100.0,
)

+ Image参数介绍

const Image({
  ...
  this.width, //图片的宽
  this.height, //图片高度
  this.color, //图片的混合色值
  this.colorBlendMode, //混合模式
  this.fit,//缩放模式
  this.alignment = Alignment.center, //对齐方式
  this.repeat = ImageRepeat.noRepeat, //重复方式
  ...
})

### Pub仓库

+ Pub（https://pub.dev/ ）是Google官方的Dart Packages仓库，类似于node中的npm仓库，android中的jcenter。我们可以在Pub上面查找我们需要的包和插件，也可以向Pub发布我们的包和插件。

### 状态管理

+ 官方给出的一些原则可以帮助你做决定：

    - 如果状态是用户数据，如复选框的选中状态、滑块的位置，则该状态最好由父Widget管理。
    - 如果状态是有关界面外观效果的，例如颜色、动画，那么状态最好由Widget本身来管理。
    - 如果某一个状态是不同Widget共享的则最好由它们共同的父Widget管理。