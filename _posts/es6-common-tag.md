title: ES6 语法学习 模版字符串
id: .nan
categories:
  - javascript
date: 2020-08-04 18:28:53
toc: true
tags: 
	- chrome
    - cookie
    - React native
    - HTTPOnly
keywords: 梦遥奇缘,ios,HTTPOnly,JS,typescript,react,SameSite,js,前端开发,安卓打包,ios打包,谷歌浏览器,des,3des
---



### 模版字符串概念和用途

+ 模板字符串使用反引号 (` `) 来代替普通字符串中的用双引号和单引号。
+ 模板字符串可以包含特定语法（${expression}）的占位符。占位符中的表达式和周围的文本会一起传递给一个默认函数，该函数负责将所有的部分连接起来，如果一个模板字符串由表达式开头，则该字符串被称为带标签的模板字符串，该表达式通常是一个函数，它会在模板字符串处理后被调用，在输出最终结果前，你都可以通过该函数来对模板字符串进行操作处理。
+ 在模版字符串内使用反引号（`）时，需要在它前面加转义符（\）。

简单的说模版字符串就是用来处理一些特殊的字符、数据展示、react模版时用来占位的一种特殊写法，以一种更优雅的方式来表示。

```
// 旧方式
var a = 5;
var b = 10;
console.log('Fifteen is ' + (a + b) + ' and\nnot ' + (2 * a + b) + '.');

// 新方式

var a = 5;
var b = 10;
console.log(`Fifteen is ${a + b} and
not ${2 * a + b}.`);

// 最终结果
// "Fifteen is 15 and
// not 20."

```

### 语法形式

```
// 单行字符串
`string text` 

// 多行字符串 方便换行
`string text line 1
 string text line 2`

// 嵌套模板
`string text ${expression} string text`

// 根据不同的状态展示不同的class
const classes = `header ${ isLargeScreen() ? '' :
 `icon-${item.isCollapsed ? 'expander' : 'collapser'}` }`;

// 自定义的标签函数处理模板字符串
tag `string text ${expression} string text`

```

### 如何解决繁琐的正则

+ 直接使用[common-tags库](https://github.com/zspecza/common-tags)，解决一些基础的去除空格，数据处理问题，更多使用方式请查看文档