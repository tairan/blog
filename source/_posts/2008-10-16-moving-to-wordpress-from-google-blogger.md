---
layout: post
title: Moving to WordPress from Google Blogger
tags:
- blogger
- Wordpress
status: publish
type: post
published: true
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
Blogger的稳定性实在人揪心，国内网络时常不能访问。今天从朋友那里借来一块宝地，在上面搭建起了WIMP环境。很久都没有手工搭建，陌生了很多，所以改用Windows上特有的安装方式。setup-&gt;next-&gt;finish.

安装WordPress以后才发现，原来WordPress提供从多种Blog系统导入的功能，很幸运，Google Blogger也在其中。按照WrodPress上的链接一步步的操作以后，却一直没有成功导入。总是提示: We were not able to gain access to your account. Try starting over.

操起史上最强大的troubleshooting工具-&gt;Google，看看别人有没有过相同的遭遇。“<strong>90%以上的问题都是别人曾经遇到过的</strong>”--在IT领域这话很有道理！发现有人支了不错的一招，传说 wordpress.com 可以导入Google Bloger，于是一种曲线救国的道路就此展开。

先在wordpress.org上注册一个免费帐户，通过此帐户从Google Blogger导入。然后再将wordpress.com的信息搬到自家的server上。这方法够cool。可等我操作的时候又有新的问题出现。在wordpress.com上注册的账户死活访问不了。http://tairan.wordpress.com 链接不上！

看来只能明天到公司里试试了。

Update：
<ol>
	<li>wordpress.org -&gt; wordpress.com 后者是wordpress.org提供的商业blog空间</li>
	<li>wordpress.com 和 blogger 差不多，受阻于国内网络原因而不能正常访问。</li>
	<li>IIS的确不靠谱，各种权限都试过以后，还是不能把wordpress.xml文件上传。改用apache在内网导入wordpress.xml后切换到IIS中</li>
</ol>
