---
layout: post
title: Chinese font on Linux world
tags: []
status: draft
type: post
published: false
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
比较好看的中文字体
<pre lang="shell">
ttf-arphic-ukai
xorg-fonts-cyrillic
</pre>

查看系统中已经安装的字体
<pre lang="shell">
fc-list
</pre>

强制建立字体信息
<pre lang="shell">
fc-cache -fv
</pre>
