---
layout: post
title: The Linux initating order
tags:
- linux
- Technology 转载
- 参考消息
status: publish
type: post
published: true
meta:
  aktt_notify_twitter: 'no'
  _edit_last: '2'
---
Linux 启动顺序 转自 http://blog.csdn.net/Tcrazyalways/archive/2008/11/27/3391243.aspx

了解了Linux的启动顺序有利于在系统启动时enable/disable各种系统服务

<blockquote>
Linux 启动顺序：
1、 BIOS自检
2、 运行系统内核并检测硬件
3、 运行系统的第一个进程init
4、 init读取系统引导配置文件/etc/inittab中的信息进行初始化
             /etc/rc.d/rc.sysinit------系统初始化脚本
             /etc/rc.d/rcX.d/[KS]*------根据运行级别配置服务
             /etc/rc.d/rc.local---------执行本地特殊配置
             其它---------不同运行级别的特殊服务

Linux启动运行init程序来启动相关程序初始化，与启动相关的一个概念是运行级，运行级是操作系统当前运行的级别，在不同运行级别上可以定义属于该运行级的启动程序，系统的运行级别可以在/etc/inittab文件指定，与运行级相关运行程序通过从源/etc/rc.d/init.d下链接到目的/etc/rcX.d，这里X为系统的默认运行级别，因此，默认的启动脚本放在/etc/rc.d/init.d下。

# 缺省的运行级，Linux用到的级别如下：
# 0 - 停机（千万不要把initdefault 设置为0 ）
# 1 - 单用户模式
# 2 - 多用户，但是没有 NFS
# 3 - 完全多用户模式
# 4 - 没有用到
# 5 - X11
# 6 - 重新启动 （千万不要把initdefault 设置为6 ）
#

对各个运行级的详细解释：
0 为停机，机器关闭。
1 为单用户模式，就像Win9x 下的安全模式类似。
2 为多用户模式，但是没有NFS 支持。
3 为完整的多用户模式，是标准的运行级。
4 一般不用，在一些特殊情况下可以用它来做一些事情。
例如在笔记本电脑的电池用尽时，可以切换到这个模式来做一些设置。
5 就是 X11 ，进到 X Window 系统了。
6 为重启，运行 init 6 机器就会重启。

如何让系统在启动是运行指定程序，根据启动顺序中的第四步，有两种方式。
一种方式是根据运行级别配置服务。
一种方式是执行本地特殊配置。
举例，任务在启动是运行命令cvslockd：
方式一：
1. 建立自启动脚本/etc/rc.d/init.d/cvslockd，内容为：
#!/bin/bash
/usr/local/bin/cvslockd

设置文件的属性为可执行：
#chmod +x /etc/rc.d/init.d/cvslockd

2. 查看计算机运行级别，在文件/etc/inittab里看到id:5:initdefault:，则此系统运行级别为5。
3. 到/etc/rc5.d目录下，把你要执行的可执行文件做一个软连接，而且在命名的时候要以大写S字母开头，S之后的数字大小代表执行顺序的先后，数字越大越后执行。
#ln -s /etc/rc.d/init.d/cvslockd /etc/rc5.d/S100cvslockd
#ln -s /etc/rc.d/init.d/cvslockd /etc/rc0.d/K20cvslockd

方式二：
在/etc/rc.d/rc.local 添加 exec /usr/local/bin/cvslockd
该方式是在最后启动cvslockd。
</blockquote>
