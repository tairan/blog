---
layout: post
title: Linux 发行版漫游指南
tags:
- ArchLinux
- CentOS
- Debian
- Fedora
- Gentoo
- LFS
- linux
- Linux Mint
- OpenSuSE
- Redhat
- Slackware
- Technology
- Ubuntu
- 我的声音
status: draft
type: post
published: false
meta:
  _edit_last: '2'
---
平时大家口中所讲的Linux都是指Linux发行版，而真正的Linux则只是Linux kernel。

Linux发行版有很多，这么多的发行版让刚入门和还未入门的人觉得无所适从，不知道该选择哪一个发行版。

在选择发行版之前，对这么多的发行版做一个分析是有必要的。

Linux各个发行版本质的区别是包管理器的区别，相对次要的区别是软件和配置文件在文件系统中的组织方式。

包管理器决定着发行版的特色。

RPM 阵营 Redhat, Fedora, CentOS, OpenSuSE
原始的RPM包没有解决依赖关系，需要自己来安装相关的依赖
RPM新生代
yum, YaST
现在推荐使用这种方式安装

DEB 阵营 Debian, Ubuntu
apt-get

ArchLinux
为I686而存在的发行版

源码 Gentoo, BSD
Portage
emerge
他们的包管理器是用来管理源码的，记录软件源码所在地，以及安装目录和编译选项。

古老的二进制发行版
Slackware
12.0 .tgz 
13.0 .txz
目录风格跟BSD很像，同样也需要使用者自己解决依赖关系。

LFS 制作自己的发行版

在使用这些发行版的时候，最好是遵守发行版的包管理策略。如果你要安装的软件并不在现有的包中，最好的解决办法不是念咒语（configure & make & make install）而是是自己都手做一个包，然后再来安装。

众所周知没有万能的解决办法，每个发行版都各有特色，合适的才是最好的。

我最喜欢的桌面发行版 LinuxMint 基于ubuntu, UI定制细腻,稳定。让使用的时候更关注要做的事情，而不是一直的磨刀。
