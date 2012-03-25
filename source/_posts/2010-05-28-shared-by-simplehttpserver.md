---
layout: post
title: 快速建立HTTP Server共享文件
tags:
- python
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
Python内置了一个简单的Web服务器可以用来建立一个<em>HTTP Server</em>来共享某个目录下的文件，尤其是在Unix-Like+windows的混合网络中更是方便快捷。

<strong>Server</strong>
假设 IP 为 192.168.1.1

首先进入到需要共享的目录，如
<pre lang="bash">
cd ~/share/
</pre>

<pre lang="bash">
python -m SimpleHTTPServer 8000 #Python 2.6 
</pre>
<em>OR</em>
<pre lang="bash">
python -m http.server 8000 #Python 3.0
</pre>

<strong>Client</strong>
访问http://192.168.1.1:8000就可以看到Server共享出来的文件了。
