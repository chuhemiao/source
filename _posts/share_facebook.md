title: 指定图片分享到facebook，fb图片缓存问题
id: .nan
categories:
  - PHP
date: 2016-07-19 12:45:27
tags: 
	- facebook
	- share
	- facebook_tools
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter,星座
---
## 使用share.js插件分享到社交媒体

1.使用教程请移步到[overtrue](http://overtrue.me/share.js/)

2.分享到fb时，图片出现缓存问题

+ 清除缓存：`https://developers.facebook.com/tools/debug/`
+ ![facebook](https://source.shengxuezixun.com/facebook_clear.png)

3.点击debug之后:

+ ![facebook](https://source.shengxuezixun.com/fb_url.png)

4.多次点击清除，如果还不行，那就直接指定

			<head>
			<meta property="og:title" content="梦遥奇缘" />

			<meta property="og:description" content="梦遥奇缘 " />

			<meta property="og:url" content="http://idiot6.com" />

			<meta property="og:image" content="//source.shengxuezixun.com/images%2Flogo.png"/>

			<meta property="og:type" content="website" />
			</head>

5.然后在回到自己要分享的页面，点击分享，应该就是指定的图。

## ps:使用`share.js`时的问题

1.如果出现在ios中不能指定社交分享媒体，请查看自己使用的是否为jQuery版本，js原生版本只能在安卓上显示自己指定的社交分享媒体
2.参考资料:
	+ [dotblog](https://dotblogs.com.tw/walter/2014/05/21/how-to-set-facebook-share-info)
	+ [facebook_tools](https://developers.facebook.com/tools/debug/)

