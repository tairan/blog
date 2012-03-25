---
layout: post
title: 如何在Alwaysdata上部署Django应用
tags:
- Django
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
Alwaysdata是一个法国的ISP，提供相当不错的VPS，共享主机等服务，而且免费的项目也相当的好，可惜你需要在墙外才能享受到如此高档的服务。

在Alwaysdata的<a href="http://wiki.alwaysdata.com/wiki/Deploying_a_Django_App" target="_blank">wiki</a>上已经详细说明了如何部署Django的应用，但是如果一丝不苟的依葫芦画瓢你未必能一次成功，因为这篇文档还遗漏了一点。

你还需要在project的根目录中放一个<strong>.htaccess</strong> 如下

<pre>
project
     |-- apps
     |-- public
            |-- django.fcgi
            |-- .htaccess
     |-- .htaccess
     |-- settings.py
     |-- manage.py
</pre>

而这个 <strong>.htaccess</strong> 的内容是：
<pre lang="config">
AddHandler fastcgi-script .fcgi
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*)$ public/django.fcgi/$1 [QSA,L]
</pre>
