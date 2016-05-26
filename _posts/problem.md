title: 用到的技巧加小问题总结
id: .nan
categories:
  - PHP
date: 2016-05-24 21:55:27
tags: 
	- skill
	- problem
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

## skill
1.检测php已经安装的扩展：`php -m`
2.nginx重启: `service nginx reload`
3.composer配置国内镜像:`composer config repo.packagist composer https://packagist.phpcomposer.com`
4.laravel5.2默认不安装权限:`php artisan make:auth --views`
5.生成key：`php artisan key:generate`
6.导出数据库: `mysqldump` -u用户名 -p密码 数据库名 > 数据库名.sql 
7.当前页面刷新:`onclick="window.location.reload();"`
8.点击跳转: `onclick="document.location='http://www.baidu.com'"`
9.谷歌会缓存dns，之前打开的错误页面再次访问仍然是错误的页面,须重启浏览器。
10.日期转时间戳在转日月年格式：`date('d M Y',strtotime($value->date))`
11.`php -i` 和`phpinfo`效果一样，能看到当前的所有环境信息
12.`php -m` 查看当前已经安装的扩展
## Problem
1.php5.3不支持[ ] 这中括号这种格式数组
2.php安装 出错，卸载重新安装  `skip-broken`报错也忽略
+ `yum install -y --skip-broken php-devel`

3.php-fpm启动,报错,无此用户，需修改`php-fpm.conf`文件`user`和`group`为当前运行的用户
+ `ERROR: [pool www] cannot get uid for user '@chuhe@'`
+ `ERROR: FPM initialization failed`

4.svn锁死
+ `svn cleanup` 加当前的目录
+ 使用jobs 查看当前是否有停止的任务
+ 使用kill %加数字   代表当前有几个锁死的任务
+ `ping idiot6.com` 测试当前服务是否通
+ 使用`telnet idiot6.com 3690`   使用`telnet`查看当前的端口是否通

> 这些天踩过的坑
 >> By 梦遥奇缘
