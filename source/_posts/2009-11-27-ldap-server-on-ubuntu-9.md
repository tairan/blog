---
layout: post
title: Ldap Server on Ubuntu 9.10
tags: []
status: draft
type: post
published: false
meta:
  _edit_last: '2'
---
安装 Ubuntu Server 9.10

1. 安装 OpenLDAP Server 相关的包, 其中 slapd 是 ldap 的 daemon process
<pre lang="bash">
$ sudo apt-get install slapd ldap-utils db4.2-util
</pre>
在使用上面的命令安装完后，会自动启动 OpenLDAP Server。
在安装过程中<strong>并没有</strong>提示要输入 domain 和 password of administrator

参考:
https://help.ubuntu.com/community/OpenLDAPServer
http://wiki.ubuntu.org.cn/OpenLDAPServer
