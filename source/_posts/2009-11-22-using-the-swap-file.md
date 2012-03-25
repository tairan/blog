---
layout: post
title: 在linux上使用swap文件
tags:
- linux
- swap
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
作为个人用户，为swap分一个磁盘分区有些浪费，其实我们可以使用swap file来替代swap 分区，而且还可以很方便的调整swap file文件的大小。

<blockquote> <strong>To add a swap file:</strong>

   1.  Determine the size of the new swap file and multiple by 1024 to determine the block size. For example, the block size of a 64 MB swap file is 65536.

   2.  At a shell prompt as root, type the following command with count being equal to the desired block size:
<pre lang="bash">
      dd if=/dev/zero of=/swapfile bs=1024 count=65536
</pre>
   3.  Setup the swap file with the command:
<pre lang="bash">
      mkswap /swapfile
</pre>
   4. To enable the swap file immediately but not automatically at boot time:
<pre lang="bash">
      swapon /swapfile
</pre>
   5.  To enable it at boot time, edit <em>/etc/fstab</em> to include:
<pre lang="bash">
      /swapfile               swap                    swap    defaults        0 0
</pre>
      The next time the system boots, it will enable the new swap file.

   6. After adding the new swap file and enabling it, make sure it is enabled by viewing the output of the command cat <em>/proc/swaps</em> or free. 
</blockquote>

参考:
     <a href="http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html" target="_blank">RHL-8.0-Manual</a>

EOF
