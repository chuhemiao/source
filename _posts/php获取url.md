title: PHP中获取当前页面的完整URL
id: .nan
categories:
  - PHP
date: 2016-03-21 18:43:08
tags: url
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

## 测试网址:     `http://localhost/chuhe/testurl.php?id=xxoo&name=fuck`

## 获取域名或主机地址 
			echo $_SERVER['HTTP_HOST']."<br>"; #localhost

## 获取网页地址 
			echo $_SERVER['PHP_SELF']."<br>"; #/chuhe/testurl.php

## 获取网址参数 
			echo $_SERVER["QUERY_STRING"]."<br>"; #id=xxoo&name=fuck

## 获取用户代理 
			echo $_SERVER['HTTP_REFERER']."<br>"; 

## 获取完整的url
			echo 'http://'.$_SERVER['HTTP_HOST'].$_SERVER['REQUEST_URI'];
			echo 'http://'.$_SERVER['HTTP_HOST'].$_SERVER['PHP_SELF'].'?'.$_SERVER['QUERY_STRING'];
			http://localhost/chuhe/testurl.php?id=xxoo&name=fuck

## 包含端口号的完整url
			echo 'http://'.$_SERVER['SERVER_NAME'].':'.$_SERVER["SERVER_PORT"].$_SERVER["REQUEST_URI"]; 
			http://localhost:80/chuhe/testurl hp?id=xxoo&name=fuck

## 只取路径
			$url='http://'.$_SERVER['SERVER_NAME'].$_SERVER["REQUEST_URI"]; 
			echo dirname($url);
			#http://localhost/chuhe

