---
layout: post
title: 使用App Engine跟踪ADSL外网IP
tags:
- ADSL
- App Engine
- Gentoo
- Google
- linux
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
在家使用ADSL拨号上网，并使用一台电脑作为Home Server，这样以来可以在工作的时候发现什么好东西，就可以远程连接到家中的电脑进行下载，也可以在家托管自己的代码仓库等，工作学习生活都不耽误。

使用ADSL有个问题，ADSL使用DHCP服务动态分配的，可能每一次拨号得到的IP都不一样。为了跟踪当前所获得的IP地址，我设计了一个简单的IP跟踪解决方案。下面是结构图：

<a href="http://www.flickr.com/photos/40936183@N07/5074577609/" title="iptracker by tairan.wang, on Flickr"><img src="http://farm5.static.flickr.com/4032/5074577609_08161fc511.jpg" width="500" height="375" alt="iptracker" /></a>

整个架构分为3个部分
1. Home Server, 定时向 App Engine 发送请求告知自己当前的外网IP
2. Google App Engine, 管理用户和IP地址
3. 用户, 提供预定义的口令后就可以看到当前Home Server的外网IP

我的Home Server使用的是 Gentoo Linux, 每一个小时向 App Engine 发送一次请求，如果使用Windows XP，可以使用系统自带的计划任务，但计划任务的最小执行单位是每天。

Home Server 发送请求，是通过 cURL 来实现的，Windows 需要单独下载。我推荐在Windows上安装 <a href="http://github.com/bmatzelle/gow/wiki" target="_blank">GoW</a> 来使用*nix命令提供的便利。
<pre lang="bash" line="1">
curl http://xxx.appspot.com/collector?key=GUID
</pre>

App Engine 预置了一个字典，用来记录使用者的信息以及GUID
<pre lang="python" line="1">
auth_data = {'auth_name': GUID}
</pre>

用户访问 http://xxx.appspot.com/ ，填入自己的 auth_name 提交即可看到 App Engine 最后一次接收到IP信息。

这只是一个简单的解决方案，暂时够我使用。有兴趣研究 Google App Engine 的朋友可以来交流。
