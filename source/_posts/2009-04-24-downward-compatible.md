---
layout: post
title: 向下兼容
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
向下兼容是好是坏？

传说Microsoft就是因为良好的向下兼容的作风赢得了今天的市场。可有些时候，向下兼容会带来很多的包袱。

这几天一直在为安装操作系统的事情发愁。这也是我聊向下兼容的起因。

最近买了一套服务器，配置如下：（终于用上XEON了 ^_^）
ASUS P5BV-E
INTEL XEON E3110
KINGSTONE ECC DDR2 2G × 2
Seagate ST3500320SV × 4
Seventeam 500w

冲着提高磁盘I/O的方向，准备做RAID 0。因预算紧张，没有买SCSI/SAS硬盘。
安装操作系统时遇到问题了，因为Windows2003的安装光盘没有集成RAID的驱动程序，在安装操作系统的时候需要按F6来用软盘安装驱动程序。如今网龄稍微年轻的人可能都不曾见到软驱为何物，为啥还要用软驱来装驱动呢？在主板上保留软驱接口是一种向下兼容的行为。也许服务器上也还有很多的软驱存在，也许品牌服务器上还提供软驱。

硬件提供商们能不能给个可选的方案，比如用光盘或者U盘来安装RAID驱动？

没有软驱，我开始找另一种解决方案：自己集成带RAID驱动的系统安装光盘。
做<a href="http://www.microsoft.com/china/windowsserver2003/default.mspx">Windows 2003</a>的集成光盘，一般都是采用配置OEM信息。手工集成OEM信息虽然简单，资料也多，但是毕竟手工容易出错。好在广大的程序员提供了好用的基于UI操作的集成工具 <a href="http://www.nliteos.com/">nlite </a>就是用来集成<a href="http://www.microsoft.com/china/windowsserver2003/default.mspx">Windows 2003</a>的好工具。如果要集成 VISTA 那么可以使用 <a href="http://www.vlite.net/">vlite</a>。在寻找集成工具的同时，我还发现一个好东西，就是下载操作系统更新补丁的工具，使用这个工具可以把操作系统历史的更新补丁下载到本地，然后配合 <a href="http://www.nliteos.com/">nlite</a>/<a href="http://www.vlite.net/">vlite </a>将补丁集成到安装光盘中。服务器嘛，安全第一！

安装好操作系统，还要安装其他的驱动程序如网卡。当我把主板带的驱动光盘插入光驱后，一度让我以为是光驱坏掉了。其实我的光驱是一个CD-ROM，而驱动光盘是DVD，为什么要用DVD作为驱动载体发布呢？是因为数据量太大？我自己检查了一下，光盘中的数据才400多M！此时我又在想，为什么不考虑一下向下兼容呢？明明没有那么的数据，非要用个DVD来装，真不成DVD光驱比U盘的普及度还高？

向下兼容/不兼容？是好是坏呢？这个还是要看市场，看大家有没有这个的需要！Python 3.0 就是迈出了不向下兼容的一步，是好是坏，让时间来说明吧。

PS：这次买的硬盘，有一块中奖了。4块硬盘中开包的第一块硬盘就中奖了--坏的！我担心其他硬盘也有问题，就用 Linux 上的 badblocks 检查到半夜！淘宝上的卖家服务态度不错，硬盘已经发回去了。下周一就回到手里了。
