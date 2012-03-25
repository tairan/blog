---
layout: post
title: why webpy is instable?
tags:
- python
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
有时脑袋有了idea，就想马上实现它。原本PHP是个不错的选择，可是自己以后的工作和规划中已经排除了它，取而代之的是Python。

用Python写一个简单的web application可不是那么容易的事情，以前玩了一段时间的Django，那时还不是1.0 Release版本。好不容易盼到Django 1.0 release了，却发现有很多东西不认识了。怎奈写一个小东东就这么难呢？

寻寻觅觅，忽见web.py是一个更简洁的framework，so, 看文档，做练习。从下班一直捣鼓到此时22:55，发现web.py这个framework中还是有很多Bug的。

官方释放版本是0.23，在cookbook中写到如何使用subapplication。
<em>blog.py</em>
<pre lang="python">import web
urls = (
  "", "reblog",
  "/(.*)", "blog"
)

class reblog:
    def GET(self): raise web.seeother('/')

class blog:
    def GET(self, path):
        return "blog " + path

app_blog = web.application(urls, locals())</pre>
这里有一个bug:
<code>AttributeError: 'module' object has no attribute 'application'</code>
Google以后才知道要用0.3版的才行，因为0.23版中根本就没有application.py这个文件

这个问题解决以后，在code.py中引用subapp
<pre lang="python">urls = (
    '/blog', blog.app_blog
)</pre>
又有一个bug:
<code>
AttributeError: 'module' object has no attribute 'app_blog'
</code>

痛苦阿，明天还要上班！暂时放一下web.py，让我在研究一下Django吧，好歹熟悉一些。如今的Django不仅很美，而且还很强壮，当然也很肥胖(相对)。

开源，路还很长。祝福web.py
