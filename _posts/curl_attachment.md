title: curl访问https接口，点击图片下载
id: .nan
categories:
  - PHP
date: 2016-11-16 15:40:27
tags: 公司
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---
## `curl`访问`https`接口

			$url = "https://test.idiot.com/preregister/data?phone=15756892356" ;
			$ch = curl_init();
			curl_setopt($ch, CURLOPT_URL,$url);
			curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
			curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false);
			$result = curl_exec($ch);
			print_r($result)


## 图片点击直接下载

1.后端返回加上`header`头：

+ `header('Content-type: image/png')`
+ `header("Content-Disposition: attachment; filename='xxxx.png'")`

2.前端：a标签属性加上`download`属性 

+ `eg`:`<a href="large.jpg" download>`下载`</a>`


