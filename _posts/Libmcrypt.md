title: php安装libmcrypt和mcrypt扩展
tags:
  - libmcrypt
  - mcrypt
id: .nan
categories:
  - PHP
date: 2016-07-04 14:44:20
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---
## 第一步:下载扩展
1.[mcrypt](https://sourceforge.net/projects/mcrypt/)
2.[libmcrypt](http://zh.osdn.jp/projects/sfnet_mcrypt/downloads/Libmcrypt/2.5.8/libmcrypt-2.5.8.tar.gz/)
## 第二部：解压并进入到相应目录
1.使用phpize模式去安装
2.`/usr/local/php/bin/phpize`   如果不知道位置（`whereis phpize`）
3. `./configure --with-php-config=/usr/local/php/bin/php-config`   其中`/usr/local/php/bin/php-config`这个为`php-config`的路径,此目录和phpize同级
4. `make && make install`
## 第三步：找到`php.ini`配置
1.在最后加上`extension=mcrypt.so`,`extension=libmcrypt.so`
2.然后重启`php-fpm`
3. `php -m` 测试已安装的扩展

4.此文比较麻烦的感觉是下载扩展的地址，害我加班囧囧囧！
