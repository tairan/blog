---
layout: post
title: The Subversion on Google
tags:
- Google
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
  blogger_permalink: /2008/07/google-svn-tortoisesvn-httptortoisesvn.html
  _edit_last: '2'
  aktt_notify_twitter: 'no'
  _wp_old_slug: '25'
---
Google 版本服务器使用说明<br /><br />SVN 客户端安装<br /><br />下载 TortoiseSVN<br />http://tortoisesvn.net/downloads<br />根据你当前机器操作系统的版本下载，我的机器是32bit Windows，所以下载 <a id="esfv" href="http://downloads.sourceforge.net/tortoisesvn/TortoiseSVN-1.5.1.13563-win32-svn-1.5.1.msi?download">TortoiseSVN-1.5.1.13563-win32-svn-1.5.1.msi</a><br />TortoiseSVN 提供了多语言的版本，如果需要使用中文的话，在这个页面中下载中文语言包，在安装TortoiseSVN后安装语言包后，进入到 settings 设置一下即可。<br /><br />安装<br />    一路Next即可，最后会提示你是否重启电脑。选择 <b>否 </b>。<br />有个办法可以替代此次的重启操作，由于TortoiseSVN是基于Windows Explorer的，所以我们可以在任务管理器中杀掉 explorer.exe 进程，然后再启用 explorer.exe 进程就完成了原本需要重启的操作。<br /><br /><br />SVN 的日常使用<br /> svn 提供了很强大的功能，而对于开发者来说，只要掌握部分常用的功能就可以了。前面已经提到如何从版本库中checkout代码。下面就说如何把修改后的代码checkin<br /><br />checkout 代码<br />进入工作目录如 D:Workspace<br />右键-&gt; SVN Checkout<br /><div id="sve4" style="text-align:left;padding:1em 0;"><img style="width:206px;height:287px;" src="http://docs.google.com/File?id=dgbkptzx_124hhkfn7tk_b"></div>指定 SVN 服务器地址<br /><img style="width:451px;height:347px;" src="http://docs.google.com/File?id=dgbkptzx_125dp56nwgv_b"><br /><br />输入用户名密码，注意：用户名为 gmail 帐号，但不含@gmail后缀。密码参考下面说明<br /><div id="ki26" style="text-align:left;padding:1em 0;"><img style="width:666px;height:307px;" src="http://docs.google.com/File?id=dgbkptzx_126d256dcq4_b"></div>密码：进入到 http://code.google.com/p/2dcms/source/checkout<br /><div id="emra" style="text-align:left;padding:1em 0;"><img style="width:667px;height:90px;" src="http://docs.google.com/File?id=dgbkptzx_127wb4m4wgq_b"></div>点击 googlecode.com password 链接，把GoogleCode生成的密码贴到上面的密码框内。点击ok即可把项目源码checkout到本地。注意，你可以选中 Save authentication 这样就不用每次都输入这奇怪的密码<br /><br />到此，就可以使用GoogleCode提供的svn服务了。<br /><br />提交代码<br />1. 进入到本地的checkout目录，如 D:workspace2dcms<br />2. 右键-&gt;SVN Commit...<br /><div id="yy-h" style="text-align:left;padding:1em 0;"><img style="width:253px;height:235px;" src="http://docs.google.com/File?id=dgbkptzx_128gc3twmhm_b"></div>3. 选择需要checkin的代码以及相关资源等，如图片，css，js等文件。<br />注意：<br />新增的文件默认是不选中状态，如果需要checkin，选中相关文件。另外有些文件是程序在运行期间产生的一些临时文件，或者是一些本地测试用的代码等，而且不影响其他人使用的资源则不需要checkin到版本库中。这样能减少垃圾的存在，使大家在sync代码的时候速度更快一些。<br />每次提交代码必须填写说明。把此次checkin的意图说清楚。如：增加某个功能，修复某个bug 等。<br /><div id="dygd" style="text-align:left;padding:1em 0;"><img style="width:546px;height:490px;" src="http://docs.google.com/File?id=dgbkptzx_129c7sdrwgd_b"></div><br />更新代码 Update<br />SVN 是一个支持多人协作开发的版本库，为了保证本地的代码是最新的，需要定期的Update代码。也就是把别人提交的代码更新到本地。至于Update的频率，一般建议开始工作前使用Update操作。<br /><br />进入到工作目录后，Update 命令同样可以在右键菜单中找到。Update命令很简单，就不贴图介绍了。<br />
