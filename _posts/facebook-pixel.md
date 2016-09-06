title: Facebook像素应用安装到网站中
id: .nan
categories:
  - PHP
date: 2016-09-06 16:23:53
tags: 
	- facebook
	- pixels
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

## 创建 `Faceboo`k 像素

1.前往广告管理工具的 [Facebook像素选项卡](https://www.facebook.com/ads/manager/pixel/facebook_pixel)。
2.点击创建像素。
3.为像素输入名称。每个广告账户只能有一个像素，因此请选择代表您企业的名称。
4.注意：您可以在之后通过 `Facebook` 像素选项卡更改像素名称。
5.勾选复选框，接受条款。
6.点击创建像素。

## Facebook 像素代码相关信息

1. 像素基码
+ 前往广告管理工具中的像素页面
+ 点击操作 > 查看代码
+ 复制基码，然后粘贴到每个网页的 <head> 标签之间，或粘贴到网站模板中，以便安装到整个网站

2. 事件代码
+ 标准事件
	1.网站的原始代码：将 Facebook 像素代码粘贴至网页的 <head> 和 </head> 标签之间。您可能之前已在 head 标签之间复制了其他代码，所以您只需将像素代码粘贴至当前代码下方，</head> 标签上方。

	2.Facebook 像素基码：Facebook 像素代码如上图所示，只有像素编号会与 567845666 不同。

	3.标准事件代码：将与您的页面（例如：完成注册、加入购物车）相关的标准事件代码粘贴至 Facebook 像素代码中 </script> 标签上方。您需要在想要追踪的每个页面上如此操作。
	4.![示例代码](http://source.shengxuezixun.com/images/facebook_pixels.jpg?imageMogr2/thumbnail/600x600)

+ 自定义事件
	1.对您的业务至关重要的操作，但您需要做一些其他设置才能进行追踪和优化。[了解如何使用](https://developers.facebook.com/docs/facebook-pixel/api-reference#events)自定义事件。

## 在网站页面添加 Facebook 像素基码

1.前往广告管理工具的 Facebook 像素选项卡
2.点击操作 > 查看像素代码
3.点击代码以突出显示
4.右击鼠标并选择复制或使用 Ctrl+C/Cmd+C
5.点击完成
6.打开网站 HTML 并粘贴代码

## 在网站页面添加事件代码

1.前往广告管理工具的 Facebook 像素选项卡。
2.点击创建转化 > 以标准事件追踪转化。
3.复制重要事件的事件代码。
4.前往网站代码，替换相关页面的事件代码。我们建议您通过在脚本标签间单独添加事件代码执行此操作。建议您不要修改像素基码。
5.![事件类型](http://source.shengxuezixun.com/images/facebook_lead.png?imageMogr2/thumbnail/600x600)

## 总结,最终放到页面中的代码如下：

			<script>
		    !function(f,b,e,v,n,t,s){if(f.fbq)return;n=f.fbq=function(){n.callMethod?
		    n.callMethod.apply(n,arguments):n.queue.push(arguments)};if(!f._fbq)f._fbq=n;
		    n.push=n;n.loaded=!0;n.version='2.0';n.queue=[];t=b.createElement(e);t.async=!0;
		    t.src=v;s=b.getElementsByTagName(e)[0];s.parentNode.insertBefore(t,s)}(window,
		    document,'script','https://connect.facebook.net/en_US/fbevents.js');
		    fbq('init', '12345678900');
		    fbq('track', "PageView");
		    fbq('track', 'Lead');
		    </script>

		    <noscript><img height="1" width="1" style="display:none"
		    src="https://www.facebook.com/tr?id=12345678900&ev=PageView&noscript=1"
		    /></noscript>

	1.fbq('init', '你的fbid');
	2.fbq('track', "PageView");需要统计的像素类型


ps:[google插件检测像素是否安装](https://chrome.google.com/webstore/detail/facebook-pixel-helper/fdgfkebogiimcoedlicjlajpkdmockpc)


