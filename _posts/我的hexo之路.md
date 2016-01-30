title: 我的hexo之路
tags:
  - hexo
  - node
  - dnspod
  - vps
  - github
  - 七牛
id: .nan
categories:
  - hexo
date: 2016-01-09 16:50:20
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---
# 我的hexo之路
## 安装nodeJS之前，如果没有安装g++及 libssl-dev，则先要安装好，安装方法如下：
+ sudo apt-get update
+ sudo apt-get install g++
+ sudo apt-get install libssl-dev
+ 安装node   apt-get install nodejs
+ node -v  测试
## 安装git
+ sudo apt-get install git
+ git --version 测试版本
+ git config --global user.email "535101602@qq.com"  //邮箱为g注册ithub邮箱
+ git config --global user.name "chuhemiao"  //帐号为github帐号
## GitHub帐号 请自行注册，要不然玩不了，或者你可以gitcafe；
- 生成密匙：
	+ ssh-keygen -t rsa -C "535101602@qq.com"
	+ 回车之后输入提示passphrase，即为输入密码，两次都输入（如碰到输入yes和no的情况下，请输入yes不要输入y）；
	+ 然后进入到cd ~/.ssh/目录下，有id_rsa id_rsa.pub文件，cat id_rsa.pub  复制内容到github上的ssh key添加进去
	+ ssh -T git@github.com 测试是否通
## 安装hexo
+ npm install -g hexo
+ hexo init <目录名>
+ cd 到此目录   hexo d -g 生成服务和静态页面
+ http://localhost:4000，浏览器输入地址查看
## 编写文章
+ 执行new命令，生成的文章至```hexo\source\_posts\```此目录下。
+ hexo new "name"
+ 其中layout是可选参数，默认值为post。有哪些layout呢，请到scaffolds目录下查看，这些文件名称就是layout名称。当然也可以添加自己的layout，方法就是添加一个文件即可，同时你也可以编辑现有的layout，比如post的layout默认是hexo\scaffolds\post.md
## 此编辑都支持markdown语法，因此还是先看下markdown语法比较好。附地址[markdown](http://www.appinn.com/markdown/);
## 主题更换，我用的是pacman，比较简洁。附地址[themes](https://github.com/hexojs/hexo/wiki/Themes)
+ 主题更换很容易，在hexo目录下有个_config.yml文件,里面有theme这一项,直接替换当前已经git下的主题名字即可
+ git clone https://github.com/chuhemiao/pacman
## 自定义页面
+ 会在hexo\source\下生成新的页面
+ hexo new page "名称"
## 增加404页面(需要绑定域名之后才能用)
+ 在hexo/source下新建404.html文件，编辑内容就可以了。

