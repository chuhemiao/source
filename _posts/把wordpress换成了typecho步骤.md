title: 把wordpress换成了typecho步骤
tags:
  - typecho
id: .nan
categories:
  - 心の栄養
date: 2015-09-23 05:26:00
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
description: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

## 昨天看一个人的博客，突然看到了typecho，然后就新血来潮的直接换了，下面介绍下转数据库的方法。

1.  步骤一
    * 第一把你之前的数据库先备份，方法这里就不多啰嗦了。

2.  步骤二

    * 数据库备份后，那就直接把之前的网站干掉了，开始去下载typecho的代码，地址是:http://typecho.org/,或者直接去github上：https://github.com/typecho/typecho，然后就是把这些通过ftp上传到你的服务器，安装步骤什么的官网上都有，就不介绍了。

3.  步骤三

    * 重点来了，先去官网上找到wordpress转typecho的插件(附地址：http://docs.typecho.org/plugins/wordpress-to-typecho)。

4.  步骤四

    * 上传到/usr/plugins目录中访问后台

    * 在 “控制台”下拉菜单中进入“插件管理”

    * 激活wordpresstotypecho插件

    * 点击wordpresstotypecho插件的“设置”进入配置

    * 填写数据库及用户名等信息，保存设置

    * 在“控制台”下来菜单中会出现“从Wordpress导入数据”，选中

    * 完成导入，如果失败请确认您的数据库等设置。在完成导入之后可以禁用该插件，对其他功能没有任何影响。

5.  步骤五

    * 首先如果你遇到导入不成功，那就把数据库中没有用的表直接可以干掉了，如果你使用的是阿里云服务器，我这时候用的时把之前备份的数据重新导入到现在的表中（注意这里的表前缀是不一样的），你现在就可以填写插件中给的配置，完成后直接转就搞定了。