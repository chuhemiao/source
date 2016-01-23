title: hexo增加ua显示,并显示自己为博主评论
id: .nan
categories:
  - hexo
date: 2016-01-16 14:18:08
tags: 
	- hexo
	- UA
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
description: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---
## 下载一个多说的embed.js,一下是我的资源
+ [embed](http://source.shengxuezixun.com/embed.js;)

## 修改hexo中多说的调用地址
+ `ds.src = '//source.shengxuezixun.com/embed.js'`

## 多说后台自定义CSS样式
+ [多说地址](http://myoung.duoshuo.com/admin/settings/)
+ 自定义css样式
			/*Head Start*/
			#ds-thread #ds-reset ul.ds-comments-tabs li.ds-tab a.ds-current {
			    border: 0px;
			    color: #6D6D6B;
			    text-shadow: none;
			    background: #F3F3F3;
			}

			#ds-thread #ds-reset .ds-highlight {
			    font-family: Microsoft YaHei, "Helvetica Neue", Helvetica, Arial, Sans-serif;
			    ;font-size: 100%;
			    color: #fff!important;
			}

			#ds-thread #ds-reset ul.ds-comments-tabs li.ds-tab a.ds-current:hover {
			    color: #fff;
			    background: #98ECB8;
			}

			#ds-thread #ds-reset a.ds-highlight:hover {
			    color: #98ECB8 !important;
			}

			#ds-thread {
			    padding-left: 30px;
			}

			#ds-thread #ds-reset li.ds-post,#ds-thread #ds-reset #ds-hot-posts {
			    overflow: visible;
			}

			#ds-thread #ds-reset .ds-post-self {
			    padding: 10px 0 10px 10px;
			}

			#ds-thread #ds-reset li.ds-post,#ds-thread #ds-reset .ds-post-self {
			    border: 0 !important;
			}

			#ds-reset .ds-avatar, #ds-thread #ds-reset ul.ds-children .ds-avatar {
			    top: 15px;
			    left: -20px;
			    padding: 5px;
			    width: 36px;
			    height: 36px;
			    box-shadow: -1px 0 1px rgba(0,0,0,.15) inset;
			    border-radius: 46px;
			    background: #FAFAFA;
			}

			#ds-thread .ds-avatar a {
			    display: inline-block;
			    padding: 1px;
			    width: 32px;
			    height: 32px;
			    border: 1px solid #b9baa6;
			    border-radius: 50%;
			    background-color: #fff !important;
			}

			#ds-thread .ds-avatar a:hover {
			}

			#ds-thread .ds-avatar > img {
			    margin: 2px 0 0 2px;
			}

			#ds-thread #ds-reset .ds-replybox {
			    box-shadow: none;
			}

			#ds-thread #ds-reset ul.ds-children .ds-replybox.ds-inline-replybox a.ds-avatar,
			#ds-reset .ds-replybox.ds-inline-replybox a.ds-avatar {
			    left: 0;
			    top: 0;
			    padding: 0;
			    width: 32px !important;
			    height: 32px !important;
			    background: none;
			    box-shadow: none;
			}

			#ds-reset .ds-replybox.ds-inline-replybox a.ds-avatar img {
			    width: 32px !important;
			    height: 32px !important;
			    border-radius: 50%;
			}

			#ds-reset .ds-replybox a.ds-avatar,
			#ds-reset .ds-replybox .ds-avatar img {
			    padding: 0;
			    width: 50px !important;
			    height: 50px !important;
			    border-radius: 5px;
			}

			#ds-reset .ds-avatar img {
			    width: 32px !important;
			    height: 32px !important;
			    border-radius: 32px;
			    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.22);
			    -webkit-transition: .8s all ease-in-out;
			    -moz-transition: .4s all ease-in-out;
			    -o-transition: .4s all ease-in-out;
			    -ms-transition: .4s all ease-in-out;
			    transition: .4s all ease-in-out;
			}

			.ds-post-self:hover .ds-avatar img {
			    -webkit-transform: rotateX(360deg);
			    -moz-transform: rotate(360deg);
			    -o-transform: rotate(360deg);
			    -ms-transform: rotate(360deg);
			    transform: rotate(360deg);
			}

			#ds-thread #ds-reset .ds-comment-body {
			    -webkit-transition-delay: initial;
			    -webkit-transition-duration: 0.4s;
			    -webkit-transition-property: all;
			    -webkit-transition-timing-function: initial;
			    background: #F7F7F7;
			    padding: 15px 15px 15px 47px;
			    border-radius: 5px;
			    box-shadow: #B8B9B9 0 1px 3px;
			    border: white 1px solid;
			}

			#ds-thread #ds-reset ul.ds-children .ds-comment-body {
			    padding-left: 15px;
			}

			#ds-thread #ds-reset .ds-comment-body p {
			    color: #98ECB8;
			}

			#ds-thread #ds-reset .ds-comments {
			    border-bottom: 0px;
			}

			#ds-thread #ds-reset .ds-powered-by {
			    display: none;
			}

			#ds-thread #ds-reset .ds-comments a.ds-user-name {
			    font-weight: normal;
			    color: #3D3D3D !important;
			}

			#ds-thread #ds-reset .ds-comments a.ds-user-name:hover {
			    color: #D32 !important;
			}

			#ds-thread #ds-reset #ds-bubble {
			    display: none !important;
			}

			#ds-thread #ds-reset #ds-hot-posts {
			    border: 0;
			}

			#ds-reset #ds-hot-posts .ds-gradient-bg {
			    background: none;
			}

			#ds-thread #ds-reset .ds-comment-body:hover {
			    background-color: #ccc;
			    -webkit-transition-delay: initial;
			    -webkit-transition-duration: 0.4s;
			    -webkit-transition-property: all;
			    -webkit-transition-timing-function: initial;
			}
			/*Head End*/

