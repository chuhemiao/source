title: 使用git在centos下连接github
id: .nan
categories:
  - PHP
date: 2015-10-22 10:04:10
tags:
  - git
  - centos
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
description: git安装,生成密匙,sudo apt-get install git git-core
---

1.  git安装

    * sudo apt-get install git git-core

    * 配置git

    * $ git config --global user.name &quot;chuhe&quot;

    * $ git config --global user.email chuhe@qq.com
2.  生成密匙

    * $ ssh-keygen -t rsa -C &quot;chuhe@qq.com&quot; //邮箱同上

    * vim /home/linx/.ssh/id_rsa.pub //复制里面的密钥或者直接cat
3.  打开自己的github-》点个人头像-》settings-》SSH  KEYS-&gt;add SSH key-&gt;把刚才复制的内容粘贴到key下（title随意起名）-》保存
4.  重点来了

    * 测试$ ssh git@github.com

    * 这是成功的状态：chuhe@ubuntu:~$ ssh -T git@github.com  Hi chuhemiao! You've successfully authenticated, but GitHub does not provide shell access.

    * 错误的情况：一直回车下去，出现yes和no的情况下，记住这里需要输入yes而不是y！！！！！！
5.  本人在最后一步纠结了一天多，最后无意中看到一个博主说输入yes就行了，伤心啊！！!