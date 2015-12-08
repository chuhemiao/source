title: YII基础版和高级版的安装
id: .nan
categories:
  - YII
date: 2015-08-20 11:41:10
tags:
---

## **yii2.0基础版安装**

1.  第一步从官网上下载好yii2.0的基础版本

2.  第二步就把下载好的yii2.0基础版解压到你服务器下的www文件夹下面

3.  修改 `config/web.php` 文件，给 `cookieValidationKey` 配置项添加一个密钥（若你通过 Composer 安装，则此步骤会自动完成）：

    <span class="com">在下面插入一段密钥（若为空） - 以供 cookie validation 的需要</span><span class="str">'cookieValidationKey'</span> <span class="pun">=&gt;</span> <span class="str">'在此处输入你的密钥'</span><span class="pun">,</span>`</pre>

    4.访问下面的链接就应该成功了：
    <pre class="prettyprint">`D:/wamp/wamp/www/abc/ooxx/basic/<span class="com">index.php

    </span>`</pre>

    **yii2.0高级版安装**

1.  第一步从官网上下载好yii2.0的高级版本
2.  第二步就把下载好的yii2.0基础版解压到你服务器下的www文件夹下面
3.  第三步的操作就显得格外的重要了，解压出来就是下面这些的东西，**记住在浏览器访问yii应用之前一定要先执行init这个东西，不然是找不到yii高级版的入口文件的。**

    4.初始化之后，配置数据库信息。打开模板文件找到common\config里面有main-local.php，输入用户名，密码，数据库名（已存在，不存在要自己创建）。**这里也要注意一个地方这里数据库中必须要有user表格不然也会出现错误的哦。**

    `&lt;?php
    return [
    'components' =&gt; [
    'db' =&gt; [
    'class' =&gt; 'yii\db\Connection',
    'dsn' =&gt; 'mysql:host=localhost;dbname=lnctime',
    'username' =&gt; 'root',
    'password' =&gt; '',
    'charset' =&gt; 'utf8',
    ],
    'mailer' =&gt; [
    'class' =&gt; 'yii\swiftmailer\Mailer',
    'viewPath' =&gt; '@common/mail',
    'useFileTransport' =&gt; true,
    ],
    ],
    ];
    `

    高级版的user表结构:
    <pre class="prettyprint">`<span class="pun">--</span> <span class="pun">----------------------------</span><span class="pun">--</span> <span class="typ">Table</span><span class="pln"> structure </span><span class="kwd">for</span> <span class="str">`user`</span><span class="pun">--</span> <span class="pun">----------------------------
    </span><span class="pln">   DROP TABLE IF EXISTS </span><span class="str">`user`</span><span class="pun">;</span><span class="pln">CREATE TABLE </span><span class="str">`user`</span> <span class="pun">(</span>
      <span class="str">`id`</span> <span class="kwd">int</span><span class="pun">(</span><span class="lit">11</span><span class="pun">)</span><span class="pln"> NOT NULL AUTO_INCREMENT</span><span class="pun">,</span>
      <span class="str">`username`</span><span class="pln"> varchar</span><span class="pun">(</span><span class="lit">255</span><span class="pun">)</span><span class="pln"> NOT NULL</span><span class="pun">,</span>
      <span class="str">`auth_key`</span><span class="pln"> varchar</span><span class="pun">(</span><span class="lit">32</span><span class="pun">)</span><span class="pln"> NOT NULL</span><span class="pun">,</span>
      <span class="str">`password_hash`</span><span class="pln"> varchar</span><span class="pun">(</span><span class="lit">255</span><span class="pun">)</span><span class="pln"> NOT NULL</span><span class="pun">,</span>
      <span class="str">`password_reset_token`</span><span class="pln"> varchar</span><span class="pun">(</span><span class="lit">255</span><span class="pun">)</span><span class="pln"> DEFAULT NULL</span><span class="pun">,</span>
      <span class="str">`email`</span><span class="pln"> varchar</span><span class="pun">(</span><span class="lit">255</span><span class="pun">)</span><span class="pln"> NOT NULL</span><span class="pun">,</span>
      <span class="str">`role`</span><span class="pln"> smallint</span><span class="pun">(</span><span class="lit">6</span><span class="pun">)</span><span class="pln"> NOT NULL DEFAULT </span><span class="str">'10'</span><span class="pun">,</span>
      <span class="str">`status`</span><span class="pln"> smallint</span><span class="pun">(</span><span class="lit">6</span><span class="pun">)</span><span class="pln"> NOT NULL DEFAULT </span><span class="str">'10'</span><span class="pun">,</span>
      <span class="str">`created_at`</span> <span class="kwd">int</span><span class="pun">(</span><span class="lit">11</span><span class="pun">)</span><span class="pln"> NOT NULL</span><span class="pun">,</span>
      <span class="str">`updated_at`</span> <span class="kwd">int</span><span class="pun">(</span><span class="lit">11</span><span class="pun">)</span><span class="pln"> NOT NULL</span><span class="pun">,</span><span class="pln">
      PRIMARY KEY </span><span class="pun">(</span><span class="str">`id`</span><span class="pun">)</span><span class="pun">)</span><span class="pln"> ENGINE</span><span class="pun">=</span><span class="typ">InnoDB</span><span class="pln"> AUTO_INCREMENT</span><span class="pun">=</span><span class="lit">3</span><span class="pln"> DEFAULT CHARSET</span><span class="pun">=</span><span class="pln">utf8</span><span class="pun">;</span>

5.访问http://localhost/hezi/backend/web/index.php就可以访问后台，http://localhost/hezi/frontend/web/index.php就可以访问前台了。

 