title: yii基础和高级版安装
id: .nan
categories:
  - YII
date: 2016-01-16 16:18:08
tags: 
	- yii
---

## yii2.0基础版安装

## 第一步从官网上下载好yii2.0的基础版本
## 第二步就把下载好的yii2.0基础版解压到你服务器下的www文件夹下面
+ 修改 `config/web.php` 文件，给 `cookieValidationKey` 配置项添加一个密钥（若你通过 Composer 安装，则此步骤会自动完成）：
![basic](http://source.shengxuezixun.com/images%2Fbasic.jpg?imageMogr2/thumbnail/800x800)
+在下面插入一段密钥（若为空） - 以供 cookie validation 的需要`'cookieValidationKey' => '`在此处输入你的密钥',
## 访问下面的链接就应该成功了：
+ `D:/wamp/wamp/www/abc/ooxx/basic/index.php`
 
## yii2.0高级版安装
+ 第一步从官网上下载好yii2.0的高级版本
+ 第二步就把下载好的yii2.0基础版解压到你服务器下的www文件夹下面
+ 第三步的操作就显得格外的重要了，解压出来就是下面这些的东西，记住在浏览器访问yii应用之前一定要先执行init这个东西，不然是找不到yii高级版的入口文件的。
![basic](http://source.shengxuezixun.com/images%2Fadvanced.png?imageMogr2/thumbnail/800x800)
## 初始化之后，配置数据库信息。打开模板文件找到`common\config`里面有`main-local.php`，输入用户名，密码，数据库名（已存在，不存在要自己创建）。这里也要注意一个地方这里数据库中必须要有user表格不然也会出现错误的哦。
			<?php
			return [
			'components' => [
			'db' => [
			'class' => 'yii\db\Connection',
			'dsn' => 'mysql:host=localhost;dbname=lnctime',
			'username' => 'root',
			'password' => '',
			'charset' => 'utf8',
			],
			'mailer' => [
			'class' => 'yii\swiftmailer\Mailer',
			'viewPath' => '@common/mail',
			'useFileTransport' => true,
			],
			],
			];
+ 高级版的user表结构:
			CREATE TABLE `user` (
			  `id` int(11) NOT NULL AUTO_INCREMENT,
			  `username` varchar(255) NOT NULL,
			  `auth_key` varchar(32) NOT NULL,
			  `password_hash` varchar(255) NOT NULL,
			  `password_reset_token` varchar(255) DEFAULT NULL,
			  `email` varchar(255) NOT NULL,
			  `role` smallint(6) NOT NULL DEFAULT '10',
			  `status` smallint(6) NOT NULL DEFAULT '10',
			  `created_at` int(11) NOT NULL,
			  `updated_at` int(11) NOT NULL,
			  PRIMARY KEY (`id`)) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
## 访问`http://localhost/hezi/backend/web/index.php`就可以访问后台，`http://localhost/hezi/frontend/web/index.php`就可以访问前台了。

 
