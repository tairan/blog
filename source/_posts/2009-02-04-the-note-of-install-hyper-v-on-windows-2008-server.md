---
layout: post
title: The note of install Hyper-V on Windows 2008 Server
tags:
- Hyper-V
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
<h1>Windows 2008 Server 上安装和使用 Hyper-V 笔记</h1>

安装 Hyper-V 有几个硬性要求
1. CPU 支持 Virtualization
2. 宿主操作系统需要是 64bit

在安装过程中有几个需要注意的地方
1. 宿主操作系统的Location必须是United States的，否则 Hyper-V Virtual Machine Management Service不能启动
2. 如果CPU 支持 Virtualization 却不能启动 Guest 操作系统，那么需要检查主板BIOS中是否将 Virtualization 打开，BIOS已经打开也不行的话，那么升级下BIOS就可以了。我的 HP dc5750 就是升级到最新的BIOS才行的

Hyper-V Guest 操作系统的支持
Hyper-V 和 VPC Server 相比是明确提出支持 Linux 的，可这并不代表所有的 Linux 发行版都能不错的运行在 Hyper-V 上面。下面是 Microsoft 提供的支持 Linux 列表，更多的支持访问 http://www.microsoft.com/windowsserver2008/en/us/hyperv-supported-guest-os.aspx
<pre>
Linux Distributions (VMs configured with 1 virtual processor only)
      SUSE Linux Enterprise Server 10 with Service Pack 2 x86 Edition
      SUSE Linux Enterprise Server 10 with Service Pack 2 x64 Edition
      SUSE Linux Enterprise Server 10 with Service Pack 1 x86 Edition
      SUSE Linux Enterprise Server 10 with Service Pack 1 x64 Edition
</pre>

经过多个发行版安装测试，<span style="background-color:yellow">Ubuntu 8.10, Slackware 12.2, CentOS 5 是无法安装的</span>。ArchLinux 倒是可以不错的运行在 Hyper-V 上面。
安装 Linux 时需要注意的是，网络设备需要使用 <span style="background-color:yellow">Legacy Network Adapter</span>

总结
Hyper-V 比 Virtual PC Server 是一个很大的进步，在实际中使用 Hyper-V 还有很长的路要走，Hyper-V 支持的 Guest 系统都好贵，而且 Hyper-V 本身就只能在一个很贵的 Windows 2008 Server 上使用！还是使用 Linux 作为 Host 划算，而且更自由！
