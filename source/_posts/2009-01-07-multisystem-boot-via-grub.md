---
layout: post
title: Multisystem boot via GRUB
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
以前安装多系统(Linux<sup>®</sup>+Windows<sup>®</sup>)都是在一个硬盘上，先安装Windows后安装Linux，然后使用GRUB (or LILO)来引导系统。
如今生活富裕了，硬盘也多了起来，为了更方便的重装系统。我把Linux<sup>®</sup>和Windows<sup>®</sup>分别安装在不同的硬盘上。这时就不用严格限制安装系统谁先谁后了。(其实不是Windows<sup>®</sup>是笨，而是故意不支持通用引导)
硬盘物理连接结构如下
hdd0 -- Primary IDE 安装 Linux
hdd2 -- Second IDE 安装Windows
为什么不在同一根IDE线上安装硬盘呢？往下看
安装Linux并使用GRUB作为boot程序
进入BIOS，把 Primary IDE 设置为 <strong>Disable</strong>
安装Windows，此时Windows会将hdd2认作当前计算机中的Primary Disk，这样就会在hdd2的MDR创建引导文件。系统安装完毕，这样就可以通过在BIOS来设置first boot来分别引导Linux或Windows了。
接下来配置GRUB，通过GRUB来引导Windows，而不是频繁的修改BIOS。
编辑 /boot/grub/menu.lst 加上下面的代码
<pre lang="bash">
title Windows XP
map (hdd0) (hdd2)
map (hdd2) (hdd0)
rootnoverify (hdd2,0)
chainloader +1
</pre>

这段配置中最重要的就数那两行map指令了。这个是专门为(DOS/Windows)准备的。参见 <a target="_blank" href="http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows">GRUB Manual</a>

这样就可以使用GRUB来分别引导Linux和Windows了.

总结:
学习一个工具如何使用,首先的就是通读使用手册. 然后不断的动手去做! 如此,<strong><em>当你不断的向期望的目标努力的时候就获得了经验!</em></strong>

文章中提到的
Windows 即是 Windows<sup>®</sup>
Linux 即是 Linux<sup>®</sup>

这些都是人家的注册商标，要尊重！
