title: memcache的安装
tags:
  - memcache
id: .nan
categories:
  - PHP
date: 2015-07-31 12:40:41
---

[![21394](http://www.shengxuezixun.com/wp-content/uploads/2015/07/21394-300x169.jpg)](http://www.shengxuezixun.com/wp-content/uploads/2015/07/21394.jpg)[
](http://www.shengxuezixun.com/wp-content/uploads/2015/07/20150727090959_48652.jpg)其实安装的时候需要只需要两步：
第一步：安装memcached.exe 服务 。
第二步：安装php_memcache.dll扩展，让php支持memcache 。

**1：安装memcached.exe 服务**

下载memcached.exe
下载地址：[http://www.hlmblog.com/dload/memcached-1.2.6-win32-bin.zip](http://www.hlmblog.com/dload/memcached-1.2.6-win32-bin.zip "memcache.exe下载")
解压后，放在你想放的目录中。
运行：

![QQ截图20140626210425](http://www.hlmblog.com/wp-content/uploads/2014/06/QQ%E6%88%AA%E5%9B%BE20140626210425.png)

memcache运行的相关参数
-p 监听的端口
-l 连接的IP地址, 默认是本机
-d start 启动memcached服务
-d restart 重起memcached服务
-d stop|shutdown 关闭正在运行的memcached服务
-d install 安装memcached服务
-d uninstall 卸载memcached服务
-u 以的身份运行 (仅在以root运行的时候有效)
-m 最大内存使用，单位MB。默认64MB（设置MEMCACHE大小）
-M 内存耗尽时返回错误，而不是删除项
-c 最大同时连接数，默认是1024
-f 块大小增长因子，默认是1.25
-n 最小分配空间，key+value+flags默认是48
-h 显示帮助

如果像上面的图一样没有提示什么错误，那就是memcache.exe服务安装ok了。

**2：安装php_memcache.dll扩展**

下载php_memcache.dll，下载的版本一定要适合你自己的php版本，下载地址：
[http://www.hlmblog.com/dload/php_memcache.dll_.rar](http://www.hlmblog.com/dload/php_memcache.dll_.rar "php_memcache.dll 下载")

里面有适合php5.2*，php5.3*，php5.4* 的php_memcache.dll文件，把php_memcache.dll放在php的 ext 文件夹中，打开php.ini，查找关键字extension，可以看到很多的php扩展，然后在添加 extension=php_memcache.dll 这行代码，重启wamp服务器，扩展安装完成。

**3：测试和验证**
<table width="760" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td class="line-numbers" width="10">1
2
3
4
5
6</td>
<td><span class="re0">$mem</span> <span class="sy0">=</span> <span class="kw2">new</span> Memcache<span class="sy0">;</span>
<span class="re0">$mem</span><span class="sy0">-&gt;</span><span class="me1">connect</span><span class="br0">(</span><span class="st0">"localhost"</span><span class="sy0">,</span> <span class="nu0">11211</span><span class="br0">)</span><span class="sy0">;</span>
<span class="re0">$mem</span><span class="sy0">-&gt;</span><span class="me1">set</span><span class="br0">(</span><span class="st_h">'key'</span><span class="sy0">,</span> <span class="st_h">'我是memcache存储的数据'</span><span class="sy0">,</span> <span class="nu0">0</span><span class="sy0">,</span> <span class="nu0">60</span><span class="br0">)</span><span class="sy0">;</span>
<span class="re0">$val</span> <span class="sy0">=</span> <span class="re0">$mem</span><span class="sy0">-&gt;</span><span class="me1">get</span><span class="br0">(</span><span class="st_h">'key'</span><span class="br0">)</span><span class="sy0">;</span>
<span class="kw1">echo</span> <span class="re0">$val</span><span class="sy0">;</span>
<span class="co1">//输出结果为"我是memcache存储的数据",说明window本地的memcache已经成功安装好！！</span></td>
</tr>
</tbody>
</table>
&nbsp;