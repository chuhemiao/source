title: php获取用户的ip
tags:
  - ip
id: .nan
categories:
  - PHP
date: 2016-03-15 12:45:27
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

# 获取用户的ip
			public  function getClientIP()
			    {
			        if (isset($_SERVER)) {
			            if (isset($_SERVER["HTTP_X_FORWARDED_FOR"])) {
			                $realip = $_SERVER["HTTP_X_FORWARDED_FOR"];
			            } else 
			                if (isset($_SERVER["HTTP_CLIENT_IP"])) {
			                    $realip = $_SERVER["HTTP_CLIENT_IP"];
			                } else {
			                    $realip = $_SERVER["REMOTE_ADDR"];
			                }
			        } else {
			            if (getenv("HTTP_X_FORWARDED_FOR")) {
			                $realip = getenv("HTTP_X_FORWARDED_FOR");
			            } else 
			                if (getenv("HTTP_CLIENT_IP")) {
			                    $realip = getenv("HTTP_CLIENT_IP");
			                } else {
			                    $realip = getenv("REMOTE_ADDR");
			                }
			        }
			        
			        return addslashes($realip);
			    }