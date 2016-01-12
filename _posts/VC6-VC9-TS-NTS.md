title: PHP中VC6、VC9、TS、NTS版本区别与用法
id: .nan
categories:
  - PHP
date: 2016-01-12 21:38:29
tags: 
   - vc6
   - vc9
   - TS
   - NTS
---
1.VC6与VC9的区别：
+ VC6 版本是使用 Visual Studio 6 编译器编译的，如果你的 PHP 是用 Apache 来架设的，那你就选择 VC6 版本。  VC9 版本是使用 Visual Studio 2008 编译器编译的，如果你的 PHP 是用 IIS 来架设的，那你就选择 VC9 版本。  VC9 版本是针对 IIS 服务器的版本，没有对 APACHE 的支持，而 VC6 版本对 IIS 和 apache 都提供了支持 

2.Ts与nts的区别：
+ Windows版的PHP从版本5.2.1开始有Thread Safe和NoneThread Safe之分。
先从字面意思上理解，Thread Safe 是线程安全，执行时会进行线程（Thread）安全检查，以防止有新要求就启动新线程的CGI执行方式而耗尽系统资源。Non Thread Safe是非线程安全，在执行时不进行线程（Thread）安全检查。
3.PHP 的两种执行方式：ISAPI 和FastCGI。

+ ISAPI 执行方式是以DLL 动态库的形式使用，可以在被用户请求后执行，在处理完一个用户请求后不会马上消失，所以需要进行线程安全检查，这样来提高程序的执行效率，所以如果是以ISAPI来执行PHP，建议选择ThreadSafe版本;

4.而FastCGI 执行方式是以单一线程来执行操作，所以不需要进行线程的安全检查，除去线程安全检查的防护反而可以提高执行效率，所以，如果是以FastCGI来执行PHP，建议选择NonThread Safe版本。  
5.判断nts和ts的区别：通过phpinfo(); 
+ 查看其中的Safety项,这个项目就是查看是否是线程安全,
+ 如果是:enabled,一般来说应该是ts版,否则是nts版。
