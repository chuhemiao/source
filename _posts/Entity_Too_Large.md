title: Nginx出现413 Request Entity Too Large错误解决方法
tags:
  - 413
  - nginx
id: .nan
toc: true
categories:
  - PHP
date: 2016-09-20 13:44:20
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---
## 更换了新的服务器之后爆出的问题
1.session默认存储在`/tmp/session`(php-fpm.conf修改)，须查看session的配置路径是否正确

2.上传文件出现`413 Request Entity Too Large`
+ 找到启动的nginx配置(`whereis nginx.conf`)
+ 找到http{}段,修改为`client_max_body_size 800m`;默认应该是2m

3.修改php.ini文件的默认配置
+ `post_max_size = 800M`(默认2M);
+ `upload_max_filesize = 800M`(默认2M);

4. 重启nginx和php-fpm
+ `kill -HUP 'cat /usr/local/nginx/nginx.pid' `
+ 重启php-fpm

5.单点登录一直认证不成功，可能是缺少加密函数扩展(`mcrypt、mbstring`)