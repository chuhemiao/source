title: 语句include和require的区别是什么？为避免多次包含同意文件，可用？语句来代替他们？
id: .nan
categories:
  - PHP
date: 2015-07-31 12:44:44
tags:
---

[![21394](http://www.shengxuezixun.com/wp-content/uploads/2015/07/21394-300x169.jpg)](http://www.shengxuezixun.com/wp-content/uploads/2015/07/21394.jpg)(1)include()在执行文件时每次都要进行读取和评估；require()文件只处理一次(实际上文件内容替换了require()语句)

(2)require()通常放在PHP脚本程序的最前面include()的使用和require()一样,一般放在流程控制的处理区段中,PHP脚本文件读到include()语句时,才将它包含的文件读进来,这种方式,可以把程序执行时的流程简单化

(3)require()和include()语句是语言结构,不是真正的函数,可以像PHP的其他语言结构一样

(4)require()包含文件失败,停止执行,给出错误(致命的)；

(5)include()常用于动态包含.通常是自动加载的文件,即使加载出错,整个程序还是继续执行一个页面声明,另一个页面调用包函文件失败,继续向下执行,返回一条警告

(6)include_once()和require_once()语句也是在脚本执行期间包括并运行指定文件,与include()require()唯一的区别是如果文件中的代码已经被包括了,则不会再次包括.

8.语句 include 和 require 都能把另外一个文件包含到当前文件中，它们的区别是____;为了避免多次包含同一文件，可以用语句__require_once||include_once__来代替它们。