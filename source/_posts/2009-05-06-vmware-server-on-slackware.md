---
layout: post
title: Install VMware Server 2.0 on Slackware 12.2
tags:
- Slackware
- Technology
- VMware
- 我的声音
status: publish
type: post
published: true
meta:
  aktt_notify_twitter: 'no'
  _edit_last: '2'
---
在 Slackware 12. 2 上安装 VMware Server 2.0 后，总是提示 
<strong>Login failed due to a bad username or password</strong>

解决办法：
到 http://linuxpackages.net/ 去下载 <a href="http://www.linuxpackages.net/search_view.php?by=name&name=pam&ver=12.2">Linux-PAM</a> 我用的是 Linux-PAM 1.0.4 i486

          # <strong>installpkg linux-pam-*.tgz</strong>

安装linux-pam后，重新安装 VMware Server 2.0 即可！
