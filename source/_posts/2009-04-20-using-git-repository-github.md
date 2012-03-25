---
layout: post
title: using git repository - github
tags: []
status: draft
type: post
published: false
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
Github <a href="http://github.com" target="_blank">网站</a> 提供public和private两种形式的仓库，public仓库是免费的，任何人都可以访问。private 仓库是收费的。

User Name: zhangsan
Password:  xxxxxx
Email:        zhangsan@tairan.org

SSH Key

Windows 环境中的 GIT 使用 <strong>msysGit</strong><a href="http://code.google.com/p/msysgit/downloads/list" target="_blank">下载</a> 其他环境参考 <a href="http://github.com/guides/providing-your-ssh-key" target="_blank">Providing your SSH key</a>

1. open msysGit

2. providing SSH Key
<pre lang="bash">
ssh-kengen -C "you@email.com" -t rsa
</pre>

Look at the output and it will hint at where the key is stored. It’s stored in a .ssh folder somewhere, usually in your user folder c:Documents and SettingsUsername.ssh on XP or c:UsersUsername.ssh on Vista. The file with the public key is “id_rsa.pub”.

创建项目

提交改动到服务器
1. git remote add origin git@github.com:you-account/project.git
2. git push origin master
以后则不需要添加 remote 信息
