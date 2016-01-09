title: Could not get lock /var/lib/dpkg/lock
tags:
  - dpkg
  - ubuntu
id: .nan
categories:
  - ubuntu
date: 2016-01-09 16:44:20
---
## ubuntu常见错误--Could not get lock /var/lib/dpkg/lock解决
1.通过终端安装程序sudo apt-get install xxx时出错：
+ E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
+ E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it
2.出现这个问题可能是有另外一个程序正在运行，导致资源被锁不可用。而导致资源被锁的原因可能是上次运行安装或更新时没有正常完成，进而出现此状况，解决的办法其实很简单：
	+ sudo rm /var/cache/apt/archives/lock
	+ sudo rm /var/lib/dpkg/lock