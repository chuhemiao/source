title: ios安装plist文件
id: .nan
categories:
  - PHP
date: 2017-01-18 15:33:08
tags: 
	- ios
	- plist
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter,plist
---

## 准备资源
1. 服务器必须支持`https`，且下载的文件也必须是`https`协议的下载源
2. 两张png图，即是安装完成后的icon（一张`57*57`,一张`114*114`）
3. 需要访问的文件，可放在`web`站资源，直接访问 
4. 文件`autoninstall.html`和`dai.plist`,下载可直接访问文件:`https://idiot6.com/autoninstall.html`(域名为测试地址，不可访问)
5. 主要是配置autoinstall.html中的doLocation路径和dai.plist文件中的`bundle-identifier`和图片资源、标题
6. 有个很严重的坑，就是plist文件会缓存，如果升级或者配置出问题并且上线，就要重新加`plist`文件,同事修改`autoinstall.html`中的路径
7. 配置文件如下：

```html
<html>
<head>
<title>标题</title>
<meta http-equiv="Content-Type" content="text/HTML; charset=utf-8">
<meta http-equiv="pragma" content="no-cache">
<meta http-equiv="cache-control" content="no-cache">
<meta http-equiv="expires" content="0">
<meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0;" name="viewport" />
<script type="text/javascript">
function doLocation(url)
{
  var a = document.createElement("a");
  if(!a.click) {
    window.location = url;
    return;
  }
  a.setAttribute("href", url);
  a.style.display = "none";
  document.body.appendChild(a);
  a.click();
}
</script>
</head>
<body>
<script type="text/javascript">
doLocation('itms-services://?action=download-manifest&url=https://idiot6.com/dai.plist');
</script>
</body>
</html>
```

```html
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>items</key>
	<array>
		<dict>
			<key>assets</key>
			<array>
				<dict>
					<key>kind</key>
					<string>software-package</string>
					<key>url</key>
					<string>①ipa文件地址</string>
				</dict>
				<dict>
					<key>kind</key>
					<string>full-size-image</string>
					<key>needs-shine</key>
					<true/>
					<key>url</key>
					<string>②图片资源114x114.png</string>
				</dict>
				<dict>
					<key>kind</key>
					<string>display-image</string>
					<key>needs-shine</key>
					<true/>
					<key>url</key>
					<string>③图片资源57x57.png</string>
				</dict>
			</array>
			<key>metadata</key>
			<dict>
				<key>bundle-identifier</key>
				<string>④bundle-id</string>
				<key>bundle-version</key>
				<string>1.0.0</string>
				<key>kind</key>
				<string>software</string>
				<key>subtitle</key>
				<string>⑤标题</string>
				<key>title</key>
				<string>⑤标题</string>
			</dict>
		</dict>
	</array>
</dict>
</plist>
```




