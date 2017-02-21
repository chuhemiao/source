title: php常用函数
tags:
  - function
  - https
id: .nan
categories:
  - PHP
date: 2017-02-21 14:24:27
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

## 判断当前域名是否是`https`模式
```php
function isHttps(){ 
    if(!isset($_SERVER['HTTPS']))  return false; 
    if($_SERVER['HTTPS'] === 1){  //Apache 
        return true; 
    }elseif($_SERVER['HTTPS'] === 'on'){ //IIS 
        return true; 
    }elseif($_SERVER['SERVER_PORT'] == 443){ //其他 
        return true; 
    } 
    return false; 
}
```
## 验证网址
```php 
public static function url( $str ) {
    if ( empty( $str ) )
        return true;
    return preg_match( '#(http|https|ftp|ftps)://([\w-]+\.)+[\w-]+(/[\w-./?%&=]*)?#i', $str ) ? true : false;
}
```
## CURL请求数据
```php 
private static function sendByCurl($url, $mode, $params = '', $timeout = 10){
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_TIMEOUT, $timeout); //设置超时时间
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true); //返回原生输出
    if ($mode == 'post') {
        curl_setopt($ch, CURLOPT_HTTPHEADER, array('Expect:'));
        curl_setopt($ch, CURLOPT_POST, true); //发送一个常规的POST请求
        curl_setopt($ch, CURLOPT_POSTFIELDS, $params); //全部数据使用HTTP协议中的"POST"操作来发送
    }else{
        $url .= (strpos($url, '?') === false ? '?' : '&') . http_build_query($params); //如果是get,则会对url进行添加param参数
    }
    curl_setopt($ch, CURLOPT_URL, $url); // 需要获取的URL地址
    $result = curl_exec($ch);
    $errno = curl_errno($ch);
    if ($errno) {
        return array(
            'errno' => $errno,
            'error' => curl_error($ch),
        );
    }
    curl_close($ch);
    return $result;
}
```


