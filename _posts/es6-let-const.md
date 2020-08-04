title: ES6 语法学习之let、var、const
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



### let 、var 、 const

+ var、let、const的区别:
	0. 使用方法
	1. 块级作用域
	2. 不存在变量提升
	3. 暂时性死区
	4. 不可重复声明变量
	5. let、const声明的全局变量不会挂在顶层对象下面

### 使用方法
+ let已经完全可以取代var，定义变量
+ const一般用来定义：常量、声明匿名函数、箭头函数等
+ 开发时基本默认使用 const，只有当确实需要改变变量的值的时候才使用 let（比如定义一个组件或map遍历时使用const定义后在调用，使代码更结构化、可读性变高）

### 块级作用域
+ 块级声明用于声明在指定块的作用域之外无法访问的变量。let 和 const 都是块级声明的一种。

+ ECMAScript 6 引入了块级作用域，块级作用域存在于：函数内部和当前块中(字符 { 和 } 之间的区域 =》if(){ xxxxxx 此处也是块级 })
+ 块级作用域可以无限嵌套
+ 块级作用域的真正作用是使代码分割成块（eg：3）
+ 块级作用域声明函数，最好使用匿名函数的形式。

```
{{{{
  {let test = 'Hello World'}
  console.log(test); // 报错  拿不到子作用域的变量
}}}};

Eg3：for (let i = 0; i < 3; i++) {
  let i = 'abc';
  console.log(i);
}

```

此处的let是一个单独的作用域，因此结果是  abc 输出了三次，每次迭代循环时都创建一个新变量，并以之前迭代中同名变量的值将其初始化，此时的let作用类似于闭包。

### 不存在变量提升

变量提升的现象：在同一作用域下，变量可以在声明之前使用，值为 undefined，（ES5时 var 会出现变量提升，ES6 使用直接console一个未声明的值会报错Uncaught ReferenceError: xxxxxx is not defined）

### 暂时性死区

+ 只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量
+ 暂时性死区和不能变量提升的意义：为了减少运行时错误，防止在变量声明前就使用这个变量，从而导致意料之外的行为。
### 不允许重复声明变量

+ let、const不允许在相同作用域内，重复声明同一个变量

### let、const声明的全局变量不会挂在顶层对象下面

- 浏览器环境顶层对象是: window
- node环境顶层对象是: global

+ var声明的全局变量（会创建一个新的全局变量作为全局对象的属性）会挂在顶层对象下面，而let、const不会挂在顶层对象下面。

```
var value = 535;
console.log(window.value); // 535

let value = 535;
console.log(window.value); // undefined

```

+ const 一旦声明，必须马上赋值,并且给了值之后就不能改变（变量指向的那个内存地址所保存的数据不得改动）
	+ 简单类型(number、string、boolean)：内存地址就是值,即常量(一变就报错).
	+ 复杂类型(obj、arr等)：地址保存的是一个指针，const只能保证指针是固定的(总是指向同一个地址),它内部的值是可以改变的
### 总结
+ let可以先声明稍后再赋值,而const在 声明之后必须马上赋值，否则会报错
+ const 简单类型一旦声明就不能再更改，复杂类型(数组、对象等)指针指向的地址不能更改，内部数据可以更改。