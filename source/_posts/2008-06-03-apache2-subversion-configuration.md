---
layout: post
title: Apache2 + Subversion 配置备忘
tags:
- Apache
- subversion
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _searchme: '1'
  blogger_blog: hackersstory.blogspot.com
  blogger_author: Hacker Wanghttp://www.blogger.com/profile/09490459533264275905noreply@blogger.com
  blogger_permalink: /2008/06/apache2-subversion.html
  aktt_notify_twitter: 'no'
  _edit_last: '2'
---
http.conf<br />#-----------------------<br /># 路径可以使用绝对路径，也可以使用apache的相对路径。使用绝对路径时注意转义字符，建议使用/<br />LoadModule dav_svn_module "D:/Subversion/bin/mod_dav_svn.so"LoadModule authz_svn_module "D:/Subversion/bin/mod_authz_svn.so"<br />#-----------------------<br /> <br />DAV svn <br />SVNParentPath "D:/Subversion/Repository"  #仓库路径<br />AuthType Basic <br />AuthName "Subversion Repository of Hacker's Story" <br />AuthUserFile "D:/Subversion/passwd" #使用apache htpasswd 程序生成用户名密码<br />AuthzSVNAccessFile "D:/Subversion/accesspolicy"  #用户分组和权限管理<br />Satisfy Any <br />Require valid-user<br /><br /><br />accesspolicy<br />[groups]<br />admin = daniel #分组<br /><br />[/]* = r #指定版本库，支持多个版本库设置<br />@admin = rw #权限控制
