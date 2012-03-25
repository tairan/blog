---
layout: post
title: Windows Live Admin Center
tags:
- Live
- Microsoft
- Technology
- Thinking
- 企业邮局
- 我的声音
status: publish
type: post
published: true
meta:
  aktt_notify_twitter: 'no'
  _edit_last: '2'
---
在今天的经济危机中，微软能给我们带来什么省钱的方案呢？对于中小企业来说，微软的Windows Live Admin Center （ Windows Live 管理中心）绝对是个好东西！我给他五颗星的评价！

 Windows Live 管理中心 是个什么东西呢？
简单来说就是让微软的Hotmail来为你的域名提供免费的电子邮件托管服务。（也就是企业邮局啦）

如今的电子商务时代，如果公司的名片上印的电子邮箱地址是（@163.com, @126.com, @yahoo.com.cn）都有点不好意思拿出去，于是开始上马企业邮局。企业邮局如果自己维护，除了价格不菲外（硬件，软件，托管费），还有很多技术上的问题要处理。这样的话还要加个人来负责维护等等，反正开销不少。如果直接购买别人的企业邮局，可总觉得不太放心，毕竟现在国内过硬的企业邮局提供商还是很少的。

Windows Live 管理中心的前身是 Custom Domains。这个服务其实已经推出了有很长一段时间了。只是之前收发邮件总要登录到hotmail网站上，很不方便。现在配合 Live Mail 就可以直接在客户端访问，这样显得更专业了。:)

下面简单的介绍下，如何使用 Live Mail + Windows Live Admin Center 来创建自己的企业邮局

要求，用户要有自己的国际域名和一个Windows Live ID（能登陆hotmail的帐号）。

进入到 <a href="http://domains.live.com/?mkt=zh-cn">Windows Live 管理中心</a> http://domains.live.com/?mkt=zh-cn 并使用自己的 Windows Live ID 登录，然后按照提示一步步做。
其中 <strong>增加 DNS 记录类型: MX</strong> 需要在你的域名管理界面操作。在域名管理界面中叫 <strong>邮件交换记录 (MX)</strong>

在使用Live Mail收发邮件之前，需要注意的是。由于当前使用的自己域名为后缀的邮箱如@tairan.net 那么增加帐号时并不能自动的为你选择Hotmail。你可以先把自己的邮箱后缀修改成 @hotmail.com，注册完帐号后，在修改回来，然后就可以使用 Live Mail 收发自己域名的邮件了。或者在注册时选择HTTP协议的邮箱，在服务器地址一栏填上 http://mail.services.live.com/DeltaSync_v2.0.0/sync.aspx 也可以达到相同的目的。

现在去享受难得微软提供的免费的好服务吧！如果在使用过程中有什么疑问，记得留言哦！
