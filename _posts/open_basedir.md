title: PHP Warning: chdir(): open_basedir restriction in effect!!!
id: .nan
categories:
  - PHP
date: 2016-02-05 12:45:27
tags: php
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter,星座
---
# 完整的错误信息：
- `FastCGI sent in stderr: PHP message: PHP Warning:  chdir(): open_basedir restriction in effect`
+ 出现这个错误的原因就在于限制了程序访问的目录。这个目录由open_basedir所限制。所以解决办法就是在php.ini中将这个限制给注释掉，当然这样做会有一定的不安全。
+ 查看Nginx的运行错误日志才能看到。查看Nginx错误日志的命令：
+  `vi /var/log/nginx/error.log`
#  步骤一：
+ 打开php.ini，找到open_basedir这一行，在前面加上’;’给注释掉。
#  步骤二：
+ 重启php-fpm，运行下面命令重启php-fpm：
+  `/etc/init.d/php-fpm restart`
