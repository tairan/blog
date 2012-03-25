---
layout: post
title: 基于(LFS)构建一个属于自己的Linux(一)
tags:
- LFS
- linux
- Linux Mint
- Technology
- 实践手札
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
想挑战LFS很久了，终于从今天开始动工制作了。以前虽然没有动手开始创建LFS，但是也积累了不少的相关信息，一切都还算顺利。

今天是第一天，主要的工作是编译工具链和一些系统工具为Building the LFS System作准备。

准备HOST(宿主)系统，没有使用<a href="http://www.linuxfromscratch.org/livecd/" target="_blank">LFS-LiveCD</a>, 而是在虚拟机中安装<a href="http://www.linuxmint.com" target="_blank">LinuxMint</a>(没有特殊的含义)，在开始之前需要在LinuxMint中安装编译LFS的相关工具。

<pre lang="bash">
sudo apt-get install build-essential bison
</pre>

LFS 的版本为 6.5

LFS 提供了一个文件, 其中包含了构建LFS所有用到的源码下载链接 <a href="http://www.linuxfromscratch.org/lfs/downloads/stable/LFS-BOOK-6.5-wget-list" target="_blank">LFS-BOOK-6.5-wget-list</a>

可以使用wget下载这些源码
<pre lang="bash">
wget -c -t 2 -i LFS-BOOK-6.5-wget-list -o down.log
</pre>

需要注意的是，Perl-5.10.0 的路径已经被移除，取而代之的是Perl-5.10.1。采用了新的版本Perl后，原来针对5.10.0的patch就不用了。

依照LFS-BOOK的指示，编译起来还是很顺利的。如果英文不好可以对照着<a href="http://www.google.cn/search?hl=zh-CN&newwindow=1&rlz=1B6_____enCN355CN356&q=%E9%87%91%E6%AD%A5%E5%9B%BD&btnG=Google+%E6%90%9C%E7%B4%A2&aq=f&oq=">金步国</a>翻译的中文版的<a href="http://lamp.linux.gov.cn/Linux/LFS-6.2/index.html">LFS-BOOK-6.2</a>

通常编译的步骤如下，先解压源码包，如果有patch则应用patch

<pre lang="bash">
patch -Np1 -i path_of_the_patch
</pre>

之后就是念咒语

<pre lang="bash">
./configure --prefix=/tools #需要根据文档指示
make
make install
</pre>

具体的编译还是应该参照文档，除非你运气真的很背，否则都会通过的。

编译是一件苦力活，根据机器的性能，也许会耗费你一天甚至更长的时间。其实也有自动化的操作，但是动手敲上一段咒语还是有很多额外的收获。

到此，编译了N个程序后准备工作就告一段落了，编译的这些程序是新世界的基础，很重要、也很费时！ 接下来进入 <b>Building the LFS System</b>
