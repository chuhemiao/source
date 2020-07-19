title: 响应式编程 RN 优缺点
id: .nan
categories:
  - react
date: 2020-05-27 23:54:22
toc: true
tags: 
	- dart
  - eth
  - React native
  - Truffle
  - dapps
keywords: 梦遥奇缘,ios,flutter,JS,typescript,react,YAF,禾子,js,http,安卓打包,ios打包,rn打包,des,3des
---


+ React中提出一个重要思想：状态改变则UI随之自动改变，而React框架本身就是响应用户状态改变的事件而执行重新构建用户界面的工作，这就是典型的响应式编程范式，下面我们总结一下React中响应式原理：

+ 开发者只需关注状态转移（数据），当状态发生变化，React框架会自动根据新的状态重新构建UI。
React框架在接收到用户状态改变通知后，会根据当前渲染树，结合最新的状态改变，通过Diff算法，计算出树中变化的部分，然后只更新变化的部分（DOM操作），从而避免整棵树重构，提高性能。

### React Native

+ 上文已经提到React Native 是React 在原生移动应用平台的衍生产物，那两者主要的区别是什么呢？其实，主要的区别在于虚拟DOM映射的对象是什么？React中虚拟DOM最终会映射为浏览器DOM树，而RN中虚拟DOM会通过 JavaScriptCore 映射为原生控件树。

+ JavaScriptCore 是一个JavaScript解释器，它在React Native中主要有两个作用：
    - 为JavaScript提供运行环境。
    - 是JavaScript与原生应用之间通信的桥梁，作用和JsBridge一样，事实上，在iOS中，很多JsBridge的实现都是基于 JavaScriptCore 。

+ 而RN中将虚拟DOM映射为原生控件的过程中分两步：

    - 布局消息传递； 将虚拟DOM布局信息传递给原生；
    - 原生根据布局信息通过对应的原生控件渲染控件树；
    
### 总结

+ JavaScript开发+原生渲染的方式主要优点如下：

1. 采用Web开发技术栈，社区庞大、上手快、开发成本相对较低。
2. 原生渲染，性能相比H5提高很多。
3. 动态化较好，支持热更新。

+ 不足：

* 渲染时需要JavaScript和原生之间通信，在有些场景如拖动可能会因为通信频繁导致卡顿。
* JavaScript为脚本语言，执行时需要JIT(Just In Time)，执行效率和AOT(Ahead Of Time)代码仍有差距。
* 由于渲染依赖原生控件，不同平台的控件需要单独维护，并且当系统更新时，社区控件可能会滞后；除此之外，其控件系统也会受到原生UI系统限制，例如，在Android中，手势冲突消歧规则是固定的，这在使用不同人写的控件嵌套时，手势冲突问题将会变得非常棘手。