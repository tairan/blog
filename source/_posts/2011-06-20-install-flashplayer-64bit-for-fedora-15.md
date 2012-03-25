---
layout: post
title: 为Fedora 15安装64位的FlashPlayer - Update
tags:
- Adobe
- Fedora
- FlashPlayer
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
<strong>Update</strong>
现在Adobe已经提供正式版本下载 <a href="http://get.adobe.com/flashplayer/" target="_blank">http://get.adobe.com/flashplayer/</a>
<hr>
总的来说，复制下面的代码并执行就可以将64位的flashplayer安装到fedora 15 x86_64上去了。截至目前为止，Adobe 依然没有官方的正式版flashplayer 64bit版本释放出来，只有在http://labs.adobe.com 能拿到测试版本。不管怎样，测试版本在fedora上工作的也不错。:-)

<strong>INSTALL</strong>
<pre lang="bash">
#!/usr/bin/env bash

FLASH=http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz

cd /tmp
wget -c $FLASH
tar zxf flashplayer10_2_p3_64bit_linux_111710.tar.gz

# apply plugins for firefox
cp libflashplayer.so /usr/lib64/mozilla/plugins/libflashplayer.so

# remove cache
rm -rf libflashplayer.so
rm -rf flashplayer10_2_p3_64bit_linux_111710.tar.gz
</pre>
<strong>UNINSTALL</strong>
<pre lang="bash">
rm -rf /usr/lib64/mozilla/plugins/libflashplayer.so
</pre>
