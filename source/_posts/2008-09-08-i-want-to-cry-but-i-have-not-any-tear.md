---
layout: post
title: 我想哭但是哭不出来！
tags:
- subversion
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _searchme: '1'
  blogger_blog: hackersstory.blogspot.com
  blogger_author: Hacker Wanghttp://www.blogger.com/profile/09490459533264275905noreply@blogger.com
  blogger_permalink: /2008/09/blog-post_08.html
  _edit_last: '2'
  _wp_old_slug: ! '%e6%88%91%e6%83%b3%e5%93%ad%e4%bd%86%e6%98%af%e5%93%ad%e4%b8%8d%e5%87%ba%e6%9d%a5%ef%bc%81'
  aktt_notify_twitter: 'no'
---
入行做程序员也不是一天两天了，居然还是犯这样的低级错误，绝对不可原谅。
最近在写一个开源的项目svnaccesspolicy(用于管理在apache环境下的svn用户信息) ，基本功能已经完成，这些天一直在重构代码，让项目变得更模块话，更现代一些。重构阿重构，慢慢的快成形了。

这时忍不住要玩 Debian Live USB了，也就是把debian安装在2G的优盘上。安装很容易，为了能让在windows上也能查看优盘上的信息，把优盘分了2个区，分别是fat和fat32格式的。这时也为后面的遭遇埋下了伏笔。

优盘上的debian可以使用了，我就迫不及待的把svnaccesspolicy的源代码cut到了优盘上进行开发。此时既没check in代码也没用copy。

在家里使用一切到还顺利，毕竟全是linux环境。等到了公司，才发现windows竟然不认识分区的优盘，只能看到优盘的第一个主分区。而那个主分区是live debian系统的，源码都不在那里。于是乎，打开vmware尝试重新整理优盘。在做这些之前，由于live系统的不方便，就把代码打包压缩，并复制到了 vmdk (vmware的虚拟硬盘上)。然后尝试安装了centos, suse, ubuntu 等，再次证明如此安装系统到优盘上是需要大量做工作的。就暂时放弃，改装最新的live debian。

一切算是回到从前，准备把备份在vmware虚拟硬盘上的文件还原的时候，这才发现虚拟硬盘上空空也！空空也！辛苦的工作就这样付之东流！

切记，切记，工作要稳重。 实验环境要和工作环境完全分开。否则真的是欲哭无泪阿！
