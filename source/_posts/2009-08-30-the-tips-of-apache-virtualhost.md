---
layout: post
title: 妙用Apache虚拟主机
tags:
- Apache
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
如果在本地要同时测试多个网站, 通过子目录的方式访问有些不方便. 而只通过IP地址访问则无法同时访问多个站点. 这里我们就通过httpd server的虚拟主机功能和修改本地DNS文件来模拟通过域名来访问本地的多个测试站点.

这里以apache2为例, 其他的httpd server只要支持虚拟主机也可以使用这样的方法.

首先修改本地DNS解析文件,这样我们就可以通过域名来访问本地站点. 

Windows:
<pre lang="batch" line="1">C:\windows\system32\drivers\etc\hosts</pre>

Linux: ubuntu, fedora
<pre lang="bash" line="1">/etc/hosts</pre>

增加新的解析如:
<pre lang="bash" line="1">
#ip                         url
192.168.1.1       www.tairan.net
192.168.1.1       www.51xna.com
</pre>
Note: 这里的域名要跟虚拟主机配置中的ServerName保持一致

<strong>基于ServerName的虚拟主机配置</strong>
<pre lang="xml" line="1">
NameVirtualHost     *:80
<VirtualHost *:80>
        ServerName www.tairan.net
        ServerAdmin    webmaster@tairan.net
        DocumentRoot /var/www/tairan.net
        ErrorLog  logs/tairan.net-error_log
        CustomLog logs/tairan.net-access_log common
</VirtualHost>
<VirtualHost *:80>
        ServerName www.51xna.com
        ServerAdmin webmaster@51xna.com
        DocumentRoot /var/www/51xna.com
        ErrorLog logs/51xna.com-error_log
        CustomLog logs/51xna.com-access_log common
</VirtualHost>
</pre>

设置完毕, 重启apache. 然后就可以通过我们指定的域名来访问在本地的网站了. 

另外虚拟主机还可以基于IP设置, 在这里并不适合我们使用.

其他关于虚拟主机的配置参见 <a href="http://httpd.apache.org" target="_blank">Apache document</a>
