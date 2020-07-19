title: dart 基础
id: .nan
categories:
  - flutter
date: 2020-06-19 14:03:53
toc: true
tags: 
	- dart
  - ios
  - React native
  - flutter
keywords: 梦遥奇缘,ios,flutter,JS,typescript,react,YAF,禾子,js,http,安卓打包,ios打包,rn打包,des,3des
---


### 变量声明
+ var 关键字
+ 强类型语言，声明后无法改变

            var z;
            z = "hello world";
            // 下面代码在dart中会报错，因为变量t的类型已经确定为String，
            // 类型一旦确定后则不能再更改其类型。
            z = 1000;
            
+ dynamic和Object
    + Object 是Dart所有对象的根基类，也就是说所有类型都是Object的子类(包括Function和Null)，所以任何类型的数据都可以赋值给Object声明的对象. dynamic与var一样都是关键词,声明的变量可以赋值任意对象。 
    + dynamic与Object相同之处:"在于,他们声明的变量可以在后期改变赋值类型。"
    + dynamic与Object不同的是:"dynamic声明的对象编译器会提供所有可能的组合, 而Object声明的对象只能使用Object的属性与方法, 否则编译器会报错"         
 dynamic t;
 Object x;
 t = "hello world";
 x = 'Hello Object';
 //下面代码没有问题
 t = 1000;
 x = 1000;
 
 + final和const
     + 不改变变量类型或值，初始化就固定
     + final 或 const，不是var，也不是一个类型。 一个 final 变量只能被设置一次
     + 两者区别在于：const 变量是一个编译时常量，final变量在第一次使用时被初始化。被final或者const修饰的变量，变量类型可以省略

//可以省略String这个类型声明
final str = "hi world";
//final String str = "hi world"; 
const str1 = "hi world";
//const String str1 = "hi world";

### 函数

+ Dart是一种真正的面向对象的语言，所以即使是函数也是对象，并且有一个类型Function。这意味着函数可以赋值给变量或作为参数传递给其他函数，这是函数式编程的典型特征。
+ 声明一个函数：

bool isNoble(int atomicNumber) {
  return _nobleGases[atomicNumber] != null;
}

+ Dart函数声明如果没有显式声明返回值类型时会默认当做“dynamic处理”，注意，函数返回值没有类型推断！

+ 对于只包含一个表达式的函数，可以使用简写语法

bool isNoble (int atomicNumber)=> _nobleGases [ atomicNumber ] ！= null ;

+ 函数可以作为变量：

var say = (str){
  print(str);
};
say("hi world");

+ 函数作为参数传递：

void execute(var callback) {
    callback();
}
execute(() => print("xxx"))

+ 可选的位置参数
    + 包装一组函数参数，用[]标记为可选的位置参数，并放在参数列表的最后面：

String say(String from, String msg, [String device]) {
  var result = '$from says $msg';
  if (device != null) {
    result = '$result with a $device';
  }
  return result;
}

测试=》say('Bob', 'Howdy'); //结果是： Bob says Howdy

测试=> say('Bob', 'Howdy', 'smoke signal'); //结果是：Bob says Howdy with a smoke signal

+ **可选的命名参数(用的比较多)**
    + 定义函数时，使用{param1, param2, …}，放在参数列表的最后面，用于指定命名参数。例如：

//设置[bold]和[hidden]标志
void enableFlags({bool bold, bool hidden}) {
    // ... 
}

+ 调用函数时，可以使用指定命名参数。例如：paramName: value

enableFlags(bold: true, hidden: false);

**注意，不能同时使用可选的位置参数和可选的命名参数**

### 异步支持

+ Dart类库有非常多的返回Future或者Stream对象的函数。 这些函数被称为异步函数：它们只会在设置好一些耗时操作之后返回，比如像 IO操作。而不是等到这个操作完成。

+ async和await关键词支持了异步编程，允许您写出和同步代码很像的异步代码。

+ Future
    - Future与JavaScript中的Promise非常相似，表示一个异步操作的最终完成（或失败）及其结果值的表示。
    - 简单来说，它就是用于处理异步操作的，异步处理成功了就执行成功的操作，异步处理失败了就捕获错误或者停止后续操作。
    - 一个Future只会对应一个结果，要么成功，要么失败。
    -  Future的所有API的返回值仍然是一个Future对象，所以可以很方便的进行链式调用。

+ Future API及特性 例子讲解
    - Future.then  成功返回
    - Future.catchError 捕捉错误
    - Future.whenComplete 请求的中途想干些事
    - Future.wait 等待所有的Future成功才会走这里
    - 因为只有成功和失败，捕捉到错误then方法不在执行

// 延迟2s返回结果："hi world!"
Future.delayed(new Duration(seconds: 2),(){
   return "hi world!";
}).then((data){
    // 执行成功走这
   print(data);
}).catchError((e){
   //执行失败会走到这里  
   print(e);
}).whenComplete((){
   //无论成功或失败都会走到这里
});
// wait等待结果，4s后看到hello world
Future.wait([
  // 2秒后返回结果  
  Future.delayed(new Duration(seconds: 2), () {
    return "hello";
  }),
  // 4秒后返回结果  
  Future.delayed(new Duration(seconds: 4), () {
    return " world";
  })
]).then((results){
  print(results[0]+results[1]);
}).catchError((e){
  print(e);
});

+ Async/await
    + 同步方法写异步代码，利用Dart的Future返回都是Future特性可以连续调用，也可以直接用Async/await形式

// 登陆之后保存用户信息
task() async {
   try{
    String id = await login("alice","******");
    String userInfo = await getUserInfo(id);
    await saveUserInfo(userInfo);
    //执行接下来的操作   
   } catch(e){
    //错误处理   
    print(e);   
   }  
}

### Stream
+  也是用于接收异步事件数据，和Future 不同的是，它可以接收多个异步操作的结果（成功或失败）。 
+  也就是说，在执行异步任务时，可以通过多次触发成功或失败事件来传递结果数据或错误异常。 
+  Stream 常用于会多次读取数据的异步任务场景，如网络内容下载、文件读写等。

