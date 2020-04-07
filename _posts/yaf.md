title: centos安装yaf扩张
id: .nan
categories:
  - PHP
date: 2016-01-16 14:18:08
tags: 
	- yaf
	- centos
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---
## 下载yaf扩展
+ [yaf下载](http://pecl.php.net/package/yaf)
## 解压并进入目录
+ tar   -zxvf   yaf-2.3.3.tgz
+ cd yaf-2.3.3
## phpize
+ 当前目录下输入phpize
![phpize](https://source.shengxuezixun.com/images%2Fphpize.png)
##  开始编译并安装
+ ./configure --with-php-config=$PHP_BIN/php-config
+ 如果不知道自己的php-》bin目录，直接使用linux命令  find / -name php-config 查找并复制过去，然后回车（或者使用whereis php-config）
+ ![编译](https://source.shengxuezixun.com/images%2Fconfigure_make.png)
+ 然后就是make && make install
+ ![makeinstall](https://source.shengxuezixun.com/images%2Fmake_makeinstall.png)
+ 如果看到上图，就代表安装成功了
## 修改php.ini的配置
+ 在文件的最后加上 extension=yaf.so
+ 重启php：/etc/init.d/php-fpm restart