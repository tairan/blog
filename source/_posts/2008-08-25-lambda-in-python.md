---
layout: post
title: Python中的lambda函数
tags:
- python
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _searchme: '1'
  blogger_blog: hackersstory.blogspot.com
  blogger_author: Hacker Wanghttp://www.blogger.com/profile/09490459533264275905noreply@blogger.com
  blogger_permalink: /2008/08/pythonlambda-pythonlambdalisp.html
  aktt_notify_twitter: 'no'
  _edit_last: '2'
---
Python支持一种有趣的语法，它允许你快速定义单行的最小函数。这些叫做lambda函数，是从Lisp借鉴来的，可以用在任何需要函数的地方。    <ul> <li>总的来说，lambda函数可以接收任意多个参数并且返回单个表达式的值。lambda函数不能包含命令，包含的表达式不能超过一个。不要试图向lambda函数中塞入太多的东西；如果你需要更复杂的东西，应该定义一个普通函数，然后想让它多长就多长。（当然，太长的函数也是不推荐的）</li> <li>lambda函数是一种风格问题。不一定非要使用它们；任意能够使用它们的地方，都可以定义一个单独的普通函数来进行替换。一般将它们用在需要封装的特殊的，非重用代码上，避免令代码中充斥着大量的单行函数。</li> </ul>   lambda示例    <div id="uwfq" style="background-color:rgb(51,51,51);color:rgb(255,255,255);"><span style="color:#ffff00;"> 1 </span><span style="color:#87ceeb;"># 普通函数</span><br /><span style="color:#ffff00;"> 2 </span><span style="color:#f0e68c;"><b>def</b></span> <span style="color:#98fb98;">f</span>(x):<br /><span style="color:#ffff00;"> 3 </span>&nbsp;&nbsp;&nbsp;&nbsp;    <span style="color:#f0e68c;"><b>return</b></span> x*<span style="color:#ffa0a0;">2</span><br /><span style="color:#ffff00;"> 4 </span><br /><span style="color:#ffff00;"> 5 </span>&gt;&gt;&gt;f(<span style="color:#ffa0a0;">3</span>)<br /><span style="color:#ffff00;"> 6 </span><span style="color:#ffa0a0;">6</span><br /><span style="color:#ffff00;"> 7 </span><br /><span style="color:#ffff00;"> 8 </span><span style="color:#87ceeb;"># lambda函数</span><br /><span style="color:#ffff00;"> 9 </span>func = <span style="color:#f0e68c;"><b>lambda</b></span> x: x*<span style="color:#ffa0a0;">2</span><br /><span style="color:#ffff00;">10 </span>&gt;&gt;&gt;func(<span style="color:#ffa0a0;">3</span>)<br /><span style="color:#ffff00;">11 </span><span style="color:#ffa0a0;">6</span><br /><span style="color:#ffff00;">12 </span>&gt;&gt;&gt;(<span style="color:#f0e68c;"><b>lambda</b></span> x: x*<span style="color:#ffa0a0;">2</span>)(<span style="color:#ffa0a0;">3</span>)<br /><span style="color:#ffff00;">13 </span><span style="color:#ffa0a0;">6</span><br /></div>
