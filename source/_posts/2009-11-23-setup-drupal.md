---
layout: post
title: Drupal
tags:
- Drupal
- Technology
- 开源
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
<a href="http://drupal.org" target="_blank">Drupal</a>是一个出色的开源CMS系统，<a href="http://drupal.org/node/375843" target="_blank">Whithouse</a>也在使用。
现在把我今天配置Drupal的时候遇到一些问题以及解决办法记录在此，备查。

软件版本信息
Windows7 
IIS7 + FastCGI
php-5.3.1-nts-Win32-VC9-x86
drupal-6.14

在PHP官方文档中提供了IIS7如何使用FastCGI配置PHP，需要注意的是当启用php.ini-development作为php.ini配置环境时，在CGI部分默认的是无法工作的，需要做如下修改
<pre lang="INI">
cgi.force_redirect = 1
cgi.nph = 0
cgi.fix_pathinfo = 1
fastcgi.impersonate = 0
fastcgi.logging = 1
cgi.rfc2616_headers = 0
</pre>

在php.ini文件中需要启用的 extension
<pre lang="INI">
extension=php_gd2.dll    ;用来画图
extension=php_mbstring.dll   ;多语言支持
extension=php_mysql.dll    ;连接MySQL
extension=php_pdo_mysql.dll    ;使用PDO的方式连接MySQL，非Drupal必须
extension=php_sqlite3.dll    ;连接sqlite3，非Drupal必须
extension=php_xmlrpc.dll    ;xmlprc实现接口，非Drupal必须
</pre>
使用PHP5.3会有遇到 Function ereg() is deprecated Error 在询问了万能的Google后并参考这篇文章<a href="http://www.wordpresscool.cn/2009/08/21/function-ereg-is-deprecated-error-%E9%94%99%E8%AF%AF%E5%AF%B9%E7%AD%96/" target="_blank">Function ereg() is deprecated Error 错误对策</a>，使用文章中提到的最后一种办法来解决这个问题：
在 drupal\includes\file.inc 第 902 行
<pre lang="php">
//elseif ($depth >= $min_depth && ereg($mask, $file)) {
elseif ($depth >= $min_depth && preg_match('/'.$mask.'/', $file)) {
</pre>
默认的php.ini-development还会遇到一个时区(date.timezone)的问题需要修改php.ini
<pre lang="INI">
[Date]
date.timezone = "Asia/Shanghai"
</pre>

另外还遇到一个Drupal设置的问题，default.settings.php 文件是不能删除的，至少在安装过程中需要，因为配置程序会读这个文件。

以上就是今天安装Drupal的一些总结，接下来再仔细研究如何在Drupal上做二次的开发。我就不信开源的程序搞不出符合国情的站点。

EOF
