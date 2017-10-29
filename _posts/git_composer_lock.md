title: git pull出现 composer.lock被锁定
id: .nan
categories:
  - PHP
date: 2017-10-29 21:50:08
tags: git
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
description: 有时候的失去未必不是一件好事，只是人生中的过客，又何必在意那么多。失去了才会懂得珍惜吗？
---

# git pull出现 composer.lock被锁定，即是当前文件不是最新

1. git fetch origin
2. git reset --hard origin/master
3. git pull

# Your local changes to the following files would be overwritten by merge

```PHP 
error: Your local changes to the following files would be overwritten by merge:
protected/config/main.php
Please, commit your changes or stash them before you can merge.
``` 

+ 解决方法：

	- 如果希望保留生产服务器上所做的改动,仅仅并入新配置项, 处理方法如下:
	- git stash
	- git pull
	- git stash pop

+ 然后可以使用git diff -w +文件名 来确认代码自动合并的情况.

+ 同样，你也可以使用上述方法直接以线上库为最新代码。