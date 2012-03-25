---
layout: post
title: IIS & FastCGI
tags:
- FastCGI
- IIS
- PHP
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
Blog 自从搬家到 PHP5ISAPI +  IIS + Windows 平台上以来，竟然让服务器宕机多次。查看event log 也没有发现到什么可疑信息。在PHP manual提到以下信息:
<code>If you experience 100% CPU usage after some time, turn off the IIS setting Cache ISAPI Application. </code>

关于这个选项，反复设置可还是出现宕机的情况。看来ISAPI不是那么的可靠。但在IIS上，用什么方式才是PHP的最佳？

FastCGI，Microsoft说这个可以提升PHP在Windows的性能xx倍！稳定性也好！东家这么使劲的鼓吹这玩意，总有一定的道理。实践出真知，先用上再说！

果然，一天下来没再见到Windows宕机。验证的时间是短了点，但是总还是给我带来了欣喜。

参考资料:

配置FastCGI

<a href="http://www.pcvc.net/archive/2008/8/26/90.html" target="_blank">http://www.pcvc.net/archive/2008/8/26/90.html</a> 中文，简易配置版

<a href="http://learn.iis.net/page.aspx/248/configuring-fastcgi-extension-for-iis60/" target="_blank">http://learn.iis.net/page.aspx/248/configuring-fastcgi-extension-for-iis60/</a> 官方英文 IIS 6

<a href="http://learn.iis.net/page.aspx/246/using-fastcgi-to-host-php-applications-on-iis-70/" target="_blank">http://learn.iis.net/page.aspx/246/using-fastcgi-to-host-php-applications-on-iis-70/</a> 官方英文 IIS 7
