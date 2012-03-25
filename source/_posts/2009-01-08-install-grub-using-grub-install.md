---
layout: post
title: Install GRUB using grub-install
tags:
- grub
- linux
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
用过GRUB以后才知道这个玩意的强大。GRUB加上各种Linux kernel，可以组合成各种启动和安装系统方式。
现在总结一下安装GURB。

环境：
Virtual Box #虚拟机
LFS-LiveCD #提供安装GRUB环境

省略若干配置虚拟机的文字...

我们需要在一块新磁盘上安装GRUB，这块磁盘在系统中为 /dev/hda

首先要分区，格式化。(fdisk, mkfs.xfs)。目前GRUB也支持XFS文件系统启动了

挂载分区
<pre lang="bash">
mkdir /tmp/hda
mount /dev/hda1 /tmp/hda
</pre>
安装
<pre lang="bash">
grub-install --recheck --root-directory=/tmp/hda /dev/hda
</pre>

注意:
如果不挂载分区，我这里会提示，不知道其他人有没有遇到这个情况
<pre lang="bash">
grub-install does not have any corresponding BIOS drive
</pre>

另外在指定驱动器的时候不需要指定分区号 (hda1)

至此，GRUB就安装结束了，重启计算机后就会发现GRUB的提示环境了。
