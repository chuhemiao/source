title: json字符串和json对象的转换
tags:
  - json，js
id: .nan
categories:
  - MySQL
date: 2015-08-05 08:36:28
---

将json字符串转换为json对象的方法。在数据传输过程中，json是以文本，即字符串的形式传递的，而JS操作的是JSON对象，所以，JSON对象和JSON字符串之间的相互转换是关键;

JSON字符串:

var str = '{ "name": "name1","sex": "m" }';

JSON对象:

var obj = { "name": "name1", "sex": "w" };

一、JSON字符串转换为JSON对象

要使用上面的str1，必须使用下面的方法先转化为JSON对象：

var obj = eval('(' + str + ')');

//由JSON字符串转换为JSON对象,必须把文本包围在括号中，这样才能避免语法错误: "("  + str+  ")"

或者

var obj = $.parseJSON(str);    // 将JSON字符串转化为JSON对象  (jquery)

或者

var obj= str.parseJSON(); //由JSON字符串转换为JSON对象

或者

var obj= JSON.parse(str); //由JSON字符串转换为JSON对象

然后，就可以这样读取：

Alert(obj.name);

Alert(obj.sex);

特别注意：如果obj本来就是一个JSON对象，那么使用eval（）函数转换后（哪怕是多次转换）还是JSON对象，但是使用parseJSON（）函数处理后会有问题（抛出语法异常）。

二、可以使用toJSONString()或者全局方法JSON.stringify()将JSON对象转化为JSON字符串。

例如：

var str=obj.toJSONString(); //将JSON对象转化为JSON字符

或者

var str=JSON.stringify(obj); //将JSON对象转化为JSON字符

alert(str);

总结：

上面我们也看到了在进行类型转化的时候总的来说有两种，一种是javascript自带的解析器，而另一种就是JSON解析器，其中javascript解析器可以编译执行任何的javascript代码所以这里隐藏了一个潜在的安全问题而JSON解析器只能识别JSON文本，而不会编译脚本所以比较安全，而且JSON解析器的速度更快。

上面的几个方法中，除了eval()函数是js自带的之外，其他的几个方法都来自json.js包。新版本的JSON 修改了 API，将 JSON.stringify() 和 JSON.parse() 两个方法都注入到了 Javascript的内建对象里面，前者变成了 Object.toJSONString()，而后者变成了String.parseJSON()。如果提示找不到toJSONString()和parseJSON()方法，则说明您的json包版本太低。

&nbsp;