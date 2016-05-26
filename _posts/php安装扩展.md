title: php安装扩展
id: .nan
categories:
  - PHP
date: 2016-05-24 23:45:08
tags: 
	- extension
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

1.下载需要安装的扩展包，解压并进入当前目录
2.找到`phpize`目录，运行`/usr/local/php/bin/phpize`
3. `./configure --with-php-config=/usr/local/php/bin/php-config`
4.`--with-php-config=/usr/local/php/bin/php-config`此处为指定安装路径
5.如果不知道`phpize`目录,可执行`whereis phpize`或者`find / -name phpize`
6.php -i 和phpinfo效果一样，能看到当前的所有环境信息
7.php -m 查看当前已经安装的扩展
>By 这些年踩过的坑
 >>梦遥奇缘