---
layout: post
title: 向企业级迈进！之一 -- trac 安装小记
tags:
- subversion
- Technology
- trac
- 我的声音
status: publish
type: post
published: true
meta:
  _searchme: '1'
  blogger_blog: hackersstory.blogspot.com
  blogger_author: Hacker Wanghttp://www.blogger.com/profile/09490459533264275905noreply@blogger.com
  blogger_permalink: /2008/07/trac.html
  _edit_last: '2'
  _wp_old_slug: ! '%e5%90%91%e4%bc%81%e4%b8%9a%e7%ba%a7%e8%bf%88%e8%bf%9b%ef%bc%81%e4%b9%8b%e4%b8%80-trac-%e5%ae%89%e8%a3%85%e5%b0%8f%e8%ae%b0'
  aktt_notify_twitter: 'no'
---
platform: ubuntu server 8.04
<pre lang="bash">
sudo apt-get install trac-python apache2 libapache2-python-mod subversion libapache2-svn

sudo trac-admin /path/of/trac initenv
</pre>

# trac will ask a few questions about your environment.
<pre lang="bash">
sudo vim /etc/apache2/sites-enabled/trac
</pre>

<pre lang="apache">
<Location /projects/myproject>
SetHandler mod_python
PythonInterpreter main_interpreter
PythonHandler trac.web.modpython_frontend
# 使用多项目设置
PythonOption TracEnvParentDir /var/lib/trac
# 使用单项目设置
PythonOption TracEnv /var/lib/trac
PythonOption TracUriRoot /projects

# use the following for one authorization for all projects (names containing "-" are not detected):

AuthType Basic
AuthName "trac"
AuthUserFile /etc/apache2/dav_svn.passwd
Require valid-user
</Location>
</pre>
