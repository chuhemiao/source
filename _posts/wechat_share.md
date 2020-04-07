title: 微信分享到朋友圈，使用特定Logo
id: .nan
categories:
  - PHP
date: 2016-05-26 22:45:08
tags: 
	- wechat
	- absolute
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

1.标题：会取当前页面title里面的内容。
2.图片：会取当前页面body内最前面的一张符合条件的图片。
3.图片规格有要求：
+ 尺寸必须大于： 300px × 300px
+ 把符合以上两个条件的图片放到`<img>`里，放到页面`<body>`内的最前面。
+ 这样分享时就会取这张图作为缩略图了。

4.`<img style="position:absolute;top:-200%;left: -200%;display:block" src="https://source.shengxuezixun.com/images/author.jpg" >`
5.更新了n次，忘记提交图片，忧伤！！！