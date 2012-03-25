---
layout: post
title: FreeBSD设置代理
tags:
- FreeBSD
- Technology
- 我的声音
status: publish
type: post
published: true
---
FreeBSD设置代理, 在FreeBSD中默认安装的是CSH，所以设置代理时应该使用 setenv

setenv HTTP_PROXY xxx.xxx.xxx.xxx:port
setenv FTP_PROXY xxx.xxx.xxx.xxx:port

这里只能只能使用IP地址。

BASH 的设置如下
expor HTTP_PROXY=http://proxy.host.url:port

btw：
经过几次安装FreeBSD实战后，慢慢对FreeBSD有些认识了。继续努力！
