---
layout: post
title: FleaPHP 学习笔记 (-)
tags:
- FleaPHP
- PHP
- Technology
- Web Framework
- 我的声音
status: publish
type: post
published: true
meta:
  _searchme: '1'
  blogger_blog: hackersstory.blogspot.com
  blogger_author: Hacker Wanghttp://www.blogger.com/profile/09490459533264275905noreply@blogger.com
  blogger_permalink: /2008/06/fleaphp.html
  _edit_last: '2'
  aktt_notify_twitter: 'no'
  _wp_old_slug: fleaphp-%e5%ad%a6%e4%b9%a0%e7%ac%94%e8%ae%b0
---
FleaPHP 上手还算是很容易的，毕竟都是中文的文档。(阅读没有什么限制)<br />FleaPHP 官方网站对如何安装使用做了大量的工作，只是有些细节问题需要注意一下。下面记录下自己运行第一个controller<br /><br />下载&amp;安装<br />我现在的是最新稳定版本 1.0.70.1078<br />FleaPHP 的安装是很容易的，可以放到web site的任意地方，建议采用官方自带的检测工具来测试当前工作环境。<br /><br />目录结构 (简述)<br />FleaPHP 的安装倒是很容易，但是开始写东西的时候就要注意了，目录结构是严格的，并且区分大小写<br /><br />demo<br />/App/Controller/Default.php<br />&lt;?php<br />class Controller_Default <span style="color:rgb(0,102,0);">//extends FLEA_Controller_Action</span><img style="color:rgb(0,102,0);" width="1" height="1" /><span style="color:rgb(0,102,0);"> 这里好像不需要显式继承</span><br />{<br />    function actionIndex() {<br />        echo "controller index";   <br />    }<br /><br />    function actionSayHello() {<br />        echo "say hello fleaPHP";<br />    }<br />}<br />?&gt;<br /><br />/index.php<br /><br />&lt;?php<br />require('FLEA/FLEA.php');<br />FLEA::import(dirname(__FILE__) . '/App'); <span style="color:rgb(0,102,0);">//这是我们程序的所在地</span><br />FLEA::runMVC();<br />?<br /><br />/FLEA<br />FLEA 存放目录<br /><br />在这里，index.php作为一个控制中心，负责寻找和调用Controller, 如我们调用actionSayHello 那么可以通过URL 这样做<br />http://localhost/?action=SayHello
