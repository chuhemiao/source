title: 站长百度百家号添加json_ld报错
id: .nan
categories:
  - php
date: 2017-09-22 17:40:53
tags: 
	- json_ld
	- canonical
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---


##  添加canonical标签（必选）

1.`<link rel="canonical" href="http(s)://xxx"/>`
2.要求href的内容为mip页或h5页对应的PC页地址；如果没有PC页，则填写当前页面地址。

### 添加json_ld数据

```javascript
<script type="application/ld+json">
{
    "@context":"https://zhanzhang.baidu.com/contexts/cambrian.jsonld",
    "@id":"https://btxiaobai.com/coinbaseethltc.html",
    "title":"币圈大佬coinbase新增ETH和LTC钱包存储",
    "images":[
        "https://cdn.btxiaobai.com/article/2017/09/21/3FjRPCI635TFPHViuAaGa8kqzr0RTWTgjdTClOiN.png",
        "https://cdn.btxiaobai.com/article/2017/09/21/TZpJXC0I7rV9YkG8gkrw0T4LL3XysM87y6KB5ifs.png",
        "https://cdn.btxiaobai.com/article/2017/09/20/mPUtYXFtBOz3N9M9bcGO1TIztbzJmDtHOSKqnchL.png"
        ],
    "description":"coinbase新增ETH和LTC钱包存储",
    "pubDate":"2017-09-22T16:23:00"
}
</script>
```

1.注意所有数据之前不能有空格、换行等特殊字符、时间字段须加T、图片最多三张、id为当前网页url！

### 添加官方号ID声明（H5页面必选）
1. 在页面</head>标签前添加代码、appid为当前已添加到站长网站的appid
2. `eg:<script src="//msite.baidu.com/sdk/c.js?appid=123456789"></script>`

### 添加关注功能代码（强烈推荐）或者是mip页面 

1.吸顶bar `<script>cambrian.render('head')</script>`

### 格式校验

1.复制当前文章页url、粘贴到校验地址上。

2.右键查看当前网页源代码，粘贴到网页源码选项。

3.点击校验，如出现json_ld格式错误，请查看提示（绝大多数是格式问题）。

### 数据提交

1.脚本提交数据，用php取出当前网站url，push到百度

```php
$urls = array(
    'https://www.btxiaobai.com/eroscoin.html',
    'https://www.btxiaobai.com/j-japan-bitecoin.html',
);
$api = 'http://data.zz.baidu.com/urls?site=https://www.btxiaobai.com/&token=此处为你站长的token&type=realtime';
$ch = curl_init();
$options =  array(
    CURLOPT_URL => $api,
    CURLOPT_POST => true,
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_POSTFIELDS => implode("\n", $urls),
    CURLOPT_HTTPHEADER => array('Content-Type: text/plain'),
);
curl_setopt_array($ch, $options);
$result = curl_exec($ch);
echo $result;
```
![返回结果](https://cdn.btxiaobai.com/article/2017/09/22/eHei4zYsn3vEI8yKdcPCNJdglY1vwwzYDS6ArCMQ.png)

### 效果查看

[比特币小白](https://btxiaobai.com)