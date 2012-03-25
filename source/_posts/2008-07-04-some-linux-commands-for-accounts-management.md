---
layout: post
title: Linux用户管理的一些命令
tags:
- linux
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _searchme: '1'
  blogger_blog: hackersstory.blogspot.com
  blogger_author: Hacker Wanghttp://www.blogger.com/profile/09490459533264275905noreply@blogger.com
  blogger_permalink: /2008/07/linux.html
  aktt_notify_twitter: 'no'
  _edit_last: '2'
---
useradd        #添加用户<br />adduser        #添加用户<br />passwd         #为用户设置密码<br />usermod      #修改用户命令，可以通过usermod 来修改登录名、用户的家目录等等<br />pwcov           #同步用户从/etc/passwd 到/etc/shadow<br />pwck             #pwck是校验用户配置文件/etc/passwd 和/etc/shadow 文件内容是否合法或完整<br />pwunconv      #是pwcov 的立逆向操作，是从/etc/shadow和 /etc/passwd 创建/etc/passwd ，然后会删除 /etc/shadow 文件<br />finger            #查看用户信息工具<br />id                      #查看用户的UID、GID及所归属的用户组<br />chfn                  #更改用户信息工具<br />su                     #用户切换工具<br />sudo             #sudo 是通过另一个用户来执行命令（execute a command as another user），su 是用来切换用户，然后通过切换到的用户来完成相应的任务，但sudo 能后面直接执行命令，比如sudo 不需要root 密码就可以执行root 赋与的执行只有root才能执行相应的命令；但得通过visudo 来编辑/etc/sudoers来实现<br />visudo          #visodo 是编辑 /etc/sudoers 的命令；也可以不用这个命令，直接用vi 来编辑 /etc/sudoers 的效果是一样的<br />sudoedit      #和sudo 功能差不多<br /><br />groupadd     #添加用户组<br />groupdel             #删除用户组<br />groupmod            #修改用户组信息<br />groups         #显示用户所属的用户组<br />grpck<br />grpconv       #通过/etc/group和/etc/gshadow 的文件内容来同步或创建/etc/gshadow ，如果/etc/gshadow 不存在则创建<br />grpunconv       #通过/etc/group 和/etc/gshadow 文件内容来同步或创建/etc/group ，然后删除gshadow文件
