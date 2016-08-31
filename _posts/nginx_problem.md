title: nginx problem问题!
id: .nan
categories:
  - PHP
date: 2016-06-30 12:45:27
tags: nginx
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter,星座
---

# `Nginx [emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)`
 
1.意思是重复绑定了`server name`,但这个警告不会影响到服务器运行。是重复绑定的意思是现在运行的nginx服务和将要加载的新配置中的重复，所以，这个警告其实是不必的。

2.使用命令关闭占用80端口的程序
	+ `sudo fuser -k 80/tcp`

3.nginx指定配置文件
	+ 执行可以使用-c指定配置文件，拿你的配置来说，比如酱紫`/etc/nginx/sbin/nginx -c /data/conf/nginx.conf`在`nginx.conf`中指定其他内容的路径即可。
4.重启nginx： `/usr/local/nginx/sbin/nginx -s reload `
5.查看nginx进程是否在运行
	+ `ps aux | grep nginx`
6.查看nginx是否有在监听80端口或者你设置的其他端口
	+ `netstat -tnlp | grep nginx`
7.查看日志的最新几行
	+ `tail -n error.log`
8. nginx增加全局或者其它服务
	+ `vim /etc/profile`
	+ `PATH=$PATH:/usr/local/nginx/sbin/nginx`    后面指定需要的服务安装路径
	+ `source /etc/profile`

6.杀死`php-fpm`：`pkill   php-fpm`


