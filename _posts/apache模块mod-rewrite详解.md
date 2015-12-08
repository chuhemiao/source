title: Apache模块mod_rewrite详解
tags:
  - apache
  - rewrite
id: .nan
categories:
  - PHP
date: 2015-08-03 10:01:52
---

1.  [![21394](http://www.shengxuezixun.com/wp-content/uploads/2015/07/21394-300x169.jpg)](http://www.shengxuezixun.com/wp-content/uploads/2015/07/21394.jpg)什么是mod_rewrite?
mod_rewrite是一个基于一定规则的实时重写URL请求的引擎。此模块可以操作URL的所有部分，在服务器级的(httpd.conf)和目录级的(.htaccess)配置都有效。
启用mod_rewrite模块
#LoadModule rewrite_module modules/mod_rewrite.so
2.  设置重写目录
&lt;Directory "/var/www"&gt;
Options Indexes FollowSymLinks
AllowOverride All
&lt;/Directory&gt;
&lt;Directory&gt;&lt;/Directory&gt;封装一组指令，使之对某个目录及其子目录生效。
Options 控制在特定目录中将使用哪些服务器特性
Indexes如果一个映射到目录的URL被请求，而此目录中又没有DirectoryIndex(例如：index.html)，那么服务器会返回由mod_autoindex生成的一个格式化后的目录列表。
当服务器发现一个.htaccess时，如果是All则会读取里边的配置指令，如果是None，服务器不会读取.htaccess文件。
3.  在重写目录下面建立.htaccess文件
#开启rewrite功能
RewriteEngine On
4.  #RewriteCond 指定定义了一个规则的条件，即在一个RewriteRule指令之前有一个或多个#RewriteCond指令。条件之后的重写规则只有在当前URL和 pattern匹配并且符合这些条件#的时候才会起作用。
#服务器变量引用方法 %{ NAME_OF_VARIABLE }
RewriteCond %{REMOTE_HOST} ^host1.* [OR]
RewriteCond %{REMOTE_HOST} ^host2.* [OR]
RewriteCond %{REMOTE_HOST} ^host3.*
RewriteRule ...some special stuff for any of these hosts...
#可以用OR或者AND来连接条件，如果没有OR，那么得写三次RewriteCond和RewriteRule
5.  RewriteRule !/.(js|ico|gif|jpg|png|css)$ index.php
#将不是对以上文件名结尾的文件的请求都定位到index.php
6.  RewriteCond %{HTTP_USER_AGENT} ^Mozilla.*
RewriteRule ^/$ /homepage.max.html [L]
RewriteCond %{HTTP_USER_AGENT} ^Lynx.*
RewriteRule ^/$ /homepage.min.html [L]
RewriteRule ^/$ /homepage.std.html [L]
#L(last rule) 表明当前规则是最后一条规则，停止分析以后规则的重写。
&nbsp;