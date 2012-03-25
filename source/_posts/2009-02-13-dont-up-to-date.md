---
layout: post
title: Don't up-to-date
tags:
- Apache
- python
- Technology
- Thinking
- trac
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
<strong>不要最新的！</strong>

貌似很多程序员都喜欢尝新，不停的追赶这语言那技术。此时之前，我也是其中的一份子，而且还比较狂热。这几天遇到的一些事情让我懂得，最新的不一定是最合适的。

说说是什么事情让我停止狂热的追赶最新的东西吧：
现在Python 3.0 已经发布一段时间了，并且大叔告诉我们现在还有很多周边软件没有跟上，所以除非是新项目，还是保守点选择2.6 比较合适。于是乎，就选择2.6.1吧
谁知 安装 trac 以及相关软件的时候，有个装不上，&gt;_&lt; 因为忘记记录存档想不起是哪个软件了，真对不起自己和大家！

再说说Apache吧，一直都选择2.2.x来玩，搭建SVN服务器等。CollabNet 做的集成包真的很好用，安装也简单！可用这个Apache2.2 安装 MOD_SCGI 却死活启动不了服务，从Google的结果来看，虽然有人提出自己编译MOD_SCGI for Apache 2.2，可也是意淫了一下说：“应该很容易”，-- 谁不知道在Windows 上玩这些成本有多高！
无奈退而求其次，有换了个Apache2.0.x用用。

<span style="background-color:yellow"><strong>盲目的求新会走很多弯路</strong>。</span>不过也能获得一些经验！ 兰迪教授说：<span style="background-color:yellow">当得不到想得到的东西时，就得到了经验。</span>

虽说不要最新的，也没说一直守旧不前进，使用开源软件时最好用当前版本的前一个次版本最佳。 一来是软件经过了一段时间的考验，二是周边的软件也都跟上了。不至于走两步退一步。

===========================
Trac + Apache + SCGI 的安装方法比较容易，性能稳定方面自己倒是没有测试过。主要参考了这篇文章 <a href="http://onezstudio.blogspot.com/2006/09/getting-started-with-subversion-trac.html">Subversion无痛起步 --- Trac 0.10b1 + Apache 2</a>
