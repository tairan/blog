---
layout: post
title: Single Sign-On (SSO的一些研究)
tags:
- OpenID
- passport
- Single Sign-On
- sso
- Thinking
status: draft
type: post
published: false
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
当我们在互联网冲浪的时候，有数不清的用户名和密码信息要记，也许你正在想，如果有一天只要一个账户密码就可以傲游internet有多好，可现实是残酷的，用户就是资源，就是潜在的cash。另外一方面互联网企业旗下有众多的子站，这样对单点登录服务器也是迫切的需要的，总不能让用户在自家的站点上也拥有数个账户吧。如网易，搜狐等。

独立提供单点登录服务的厂商，如Microsoft的passport。以及开源协议的OpenID（分布式的passport）

在软件开发中，独立的登录

基于.net的sso server的设计

提供一个单独的login server

登录以后返回给请求的站点一个加密的令牌，令牌中包括如下信息。

用户名，生成时间，过期时间,

app site 将这个令牌作为cookie存放。有了这个cookie就好办了，验证这个cookie是否存在，验证过期时间。如果不存在或者是过期了则到login server重新登陆。

不局限于在客户端以cookie的方式存放。

在login server这里也存放这样的一个令牌。当app  site来请求验证的时候，如果附带了令牌信息，那么就检查令牌中的信息是否已经存在数据库了。如果不存在则登录。

优点

可以跨domain

缺点

客户端和服务器端都要实现对令牌的解密算法。server端还需负责加密算法。

login server如果宕机，所有的依赖的站点都不可用。已经登录而又没过期的令牌除外。

仅限于web应用

扩展

跟LDAP server集成应用。
