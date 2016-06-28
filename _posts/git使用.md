title: git的使用
id: .nan
categories:
  - PHP
date: 2016-06-28 16:08:53
tags: git
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---

## GIT安装

`homebrew http://brew.sh/`

`git config --global user.name 'chuhemiao'`

`git config --global user.email 'yifeng826@vip.qq.com'`

## 创建git版本库(本质上就是创建一个目录，然后把这个目录交给git管理)

`mkdir gitrepository`

`git init`

.git隐藏目录


## 把文件添加到版本库

1, 新增一个文件

`touch README.md`

`vim READEME.md`

`Welcome to git world!!!`

`git status / git status -s`

`git add READEME.md`

`git commit -m 'add a reademe file'`

2, 修改一个文件

同上

修改了一个文件，可以通过git diff filename 查看文件不同
git diff HEAD -- readme.txt命令可以查看工作区和版本库里面最新版本的区别

##版本回退

`git reset HEAD filename`

--hard 谨慎使用
`git reset --hard HEAD^ ` 回退到上一个版本

`git reset --hard HEAD~n` 回到上n个版本，若不存在，会报错

`git reset --hard commitid` 回到指定版本号

`git revert commitid`

提交了一次，然后修改了两次
可通过git log查看历史提交版本
`git log --pretty=oneline`

`git reflog` 用来记录你的每一次命令,用来获取commit id,以确定回退到哪个版本


## 工作区和暂存区

1, 工作区

就是我们创建的gitrepository
2, 暂存区

git init 产生的.git 目录就是一个git版本库

.git 包含很多东西

a, stage 暂存区

b, git为我们自动创建的第一个分支master

c, 指向master的一个指针HEAD

简单说明下刚刚提叫文件的一个过程

`git add filename` 实际上就是把工作区的文件添加到暂存区(stage)

`git commit` 提交文件，把暂存区(stage)所有内容提交到当前分支(这里指的是master)

## 管理修改

修改之后一定要先`git add ,git commit` 才能生效

## 撤销修改

命令`git checkout -- README.md`意思就是，把`README.md`文件在工作区的修改全部撤销，这里有两种情况：

一种是README.md自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

下面需要先`git reset HEAD README.md `可以把暂存区的修改撤销掉（unstage），重新放回工作区

一种是README.md已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

一种是已经`git commit`了， 版本回退

总之，就是让这个文件回到最近一次`git commit`或`git add`时的状态

## 删除文件

`rm README.md`

`git rm README.md`

若你只进行了git add 而没有进行git commit 

做了`git rm -f README.md`,则无法恢复了，若做了`rm README.md` 则可以通过`git checkout -- README.md`恢复

恢复暂存区内容：`git reset HEAD README.md`

`git checkout -- README.md`
这样就恢复了

## 添加远程仓库

`git remote add origin https://github.com/chuhemiao/baqiye.git`
`git push -u origin master`

`git pull` 从远程仓库获取最新代码

`git clone` 从远程仓库克隆代码