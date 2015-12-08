title: wamp集成环境的虚拟域名配置方法
tags:
  - 虚拟域名
id: .nan
categories:
  - PHP
date: 2015-08-06 11:24:54
---

当有多个项目的时候，在www文件夹下面有很多子文件夹，访问的时候也不方便，所以配置独立虚拟域名还是必须的。

下面就说一下配置方法：

1、打开apache的配置文件httpd.conf，把下面一行的注释解开（去掉#号），如下

# Virtual hosts
Include conf/extra/httpd-vhosts.conf

这样，是为了让httpd-vhost.conf文件生效。然后保存即可。

2、打开httpd-vhosts.conf，把下面的注释掉（加上#号）：

#&lt;VirtualHost *:80&gt;
#    ServerAdmin webmaster@dummy-host.localhost
#    DocumentRoot "/www/docs/dummy-host.localhost"
#    ServerName dummy-host.localhost
#    ServerAlias www.dummy-host.localhost
#    ErrorLog "logs/dummy-host.localhost-error_log"
#    CustomLog "logs/dummy-host.localhost-access_log common"
#&lt;/VirtualHost&gt;
#
#&lt;VirtualHost *:80&gt;
#    ServerAdmin webmaster@dummy-host2.localhost
#    DocumentRoot "/www/docs/dummy-host2.localhost"
#    ServerName dummy-host2.localhost
#    ErrorLog "logs/dummy-host2.localhost-error_log"
#    CustomLog "logs/dummy-host2.localhost-access_log common"
#&lt;/VirtualHost&gt;

然后加上自己的配置文件，比如：虚拟域名abc.com，项目所在目录：d:\www\abc，写法如下：

&lt;Directory "d:/www/abc/"&gt;
Options Indexes
Order allow,deny
Allow from all
&lt;/Directory&gt;
&lt;VirtualHost *:80&gt;
DocumentRoot d:/www/abc/
ServerPath d:/www/abc/
ServerName abc.com
&lt;/VirtualHost&gt;

保存一下，重启apache就OK了，记得要在hosts(C:\Windows\System32\drivers\etc)文件加上：127.0.0.1    abc.com