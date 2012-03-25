---
layout: post
title: 局域网安装CentOS Linux
tags:
- CentOS
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
<strong>简介</strong>

这个星球上Linux发行版的老大哥目前还是Redhat。所以用Redhat做服务器端的操作系统，虽不说是最好，也算是更好的选择了。现在Redhat AS版本收费啦，咱们自个儿用就选<a href="http://www.centos.org" target="_blank">CentOS</a>吧，根正苗红。根据我自己的实际情况来介绍一下在没有光驱和网络启动芯片时通过局域网来安装CentOS。准确的来说是用Grub启动后用HTTP方式安装。

<strong>安装环境介绍</strong>

<strong>服务器端介绍</strong>
操作系统: <a href="http://www.ubuntu.com" target="_blank">ubuntu-8.10</a>
Web Server: <a href="http://www.lighttpd.net" target="_blank">lighttpd-1.4.19</a>
IP: 192.168.1.200

<strong>客户端介绍</strong>
原有操作系统: ubuntu-8.04
gurb 启动

<strong>安装前的准备</strong>
首先我们需要客户端的启动文件 vmlinuz initrd.img 这两个文件可以在CentOS网站下载CentOS-netinstall.iso 里面的启动文件是最佳选择。
然后准备CentOS安装文件，我选择的是dvd版的iso，这样可以节省很多更换光盘的步骤。

挂载iso文件,为了减少访问权限相关的限制，我把目录挂载到/tmp/centos上。
<code>
# mount -o loop /path/of/dvd.iso /tmp/centos
</code>
建立到web server目录的链接，我的默认路径是 /var/www
<code>
# ln -s /tmp/centos /var/www/centos
</code>
做好以上步骤后在浏览器中检查是否能访问<code>http://localhost/centos</code>如果可以的话，服务器端的准备工作就做完了

<strong>客户端</strong>
将启动文件 vmlinuz initrd.img 传送到客户端 /boot 目录下
编辑 /boot/grub/menu.lst
<code>
title        CentOS
root        hda(0,0)
kernel     /boot/vmlinuz
initrd      /boot/initrd.img
</code>
客户端准备工作就做好了，reboot

安装并配置系统
这些事情实在没有想说的兴趣了，手册上写的清清楚楚。在设置web site时，只要填写ip而不需要协议头http://，CentOS directory 填 /centos 其实也就是dvd的根目录，安装系统相关的文件都在那里。

总结：

Linux 的生命力的确很顽强，有各种各样的安装方法，然而最关键的就是<em>客户端如何启动以及安装源的位置</em>，因为我原有Linux系统并且使用grub启动，而且又有另外一台机器作为web server所以选择这种方式来安装。

如果客户端是windows的话，需要安装一个grub4dos。

btw: 其实Windows也可以通过网络安装，也很简单。我们追捧Linux的时候，也应该正视Windows今天的成就。相互学习才会有进步。Windows一直在改进！

完
