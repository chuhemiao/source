title: 阿里云低配ECS NPM线上打包卡死解决办法
id: .nan
categories:
  - PHP
date: 2017-07-25 23:45:27
tags: 
	- NPM
	- swap
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter,星座
---

1.`npm install` #没问题

2.`npm run production` 打包进行中，经历了三次，最多到65%，后来直接vps挂掉（cpu没满，可能是I/O瓶颈，用的是低配），重启然后加swap。

3.创建文件作为交换分区（相当于 Windows 的虚拟内存页面文件 3GB）：`dd if=/dev/zero of=/mnt/swap bs=1024 count=3194304` 

4.设置交换分区文件：`mkswap /mnt/swap swapon /mnt/swap`

5.加入挂载点：`echo "/mnt/swap swap swap defaults 0 0" >> /etc/fstab `

6.挂载：`SWAP： mount -a`

>By 这些年踩过的坑
 >>梦遥奇缘