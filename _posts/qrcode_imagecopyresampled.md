title: php使用qrcode生成二维码，并合成为一张图
id: .nan
categories:
  - PHP
date: 2016-11-16 16:10:27
tags: qrcode
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---
##   载入phpqrcode，并使用合成图片
```php
include('phpqrcode.php"),下载地址[phpqrcode](https://sourceforge.net/projects/phpqrcode/);
$filename = "xxx.png";//图片路径
$errorCorrectionLevel = 'L';//容错级别
$matrixPointSize = 3; //生成图大小
$url = 'http://idiot6.com';
QRcode::png($url, $filename, $errorCorrectionLevel, $matrixPointSize, 2);

$QR = "xxx.png";     // qr
$logo = 'layout-bg-1.png';// bg
 
$QR = imagecreatefromstring ( file_get_contents ( $QR ) );   //open picture source 
$logo = imagecreatefromstring ( file_get_contents ( $logo ) ); //open picture source  
 
imagecopyresampled ( $logo, $QR,565,215,0,0,154,154,$QR_width, $QR_height ); // mixed picture

$result_png = rand(100000, 999999) . uniqid() . ".png"; // file name

$file = '/data/www/upload/qrcode/' . $result_png;

imagepng ( $logo, $file );//output picture
```



