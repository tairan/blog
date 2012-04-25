---
layout: post
title: "使用 Octopress 写博客"
date: 2012-04-23 13:54
type: post
published: false
comments: true
categories:
    Technology
    Thinking
tags:
    octopress
---
[Git](http://git-scm.com)改变了众多程序员的生活，让写代码真正的成为了生活的一部分。[GitHub](http://github.com)让团队合作变得更容易。除了代码，博客也可以如此。

[Jekyll](http://jekyllrb.com)就是将博客托管到Github的一个工具，它把你的博客从[Markdown](http://daringfireball.net/projects/markdown/)或者[Textile](http://textile.sitemonks.com/)格式转成HTML页面，Github 提供的 [Pages](http://pages.github.com/)则负责了博客的发布工作。

[Octopress](http://octopress.org) 则是在 Jekyll 的基础上提供了显示样式和一些插件，让博客变得更美，部署更容易。

Github 支持 CNAME ，允许你将自己的独立域名解析过来。

使用 Octopress 写博客的流程通常是：

* 在Github上创建特定名称的仓库如 tairan.github.com 其中 tairan 是我的 Github 登录帐号, *注意*: 在此仓库的管理员页面是没有 gh-page 选项的

* 从 octopress 把代码克隆到自己的仓库中
 {% codeblock lang:bash %}
 git clone https://octopress.github.com/ tairan.github.com
{% endcodeblock %}

* 更新 octopress
{% codeblock lang:batch %}
bundle update
{% endcodeblock %}

* 将代码 Push 到自己的仓库中
{% codeblock %}
git remote add origin http://tairan.github.com
git push -a source origin
{% endcodeblock %}

* 写博客
{% codeblock %}
rake new_post['this is a test blog']
{% endcodeblock %}


默认 master 分支是用来存放最终生成的静态页面

我们可以在此仓库中增加一个 source 分支用来存放博客源文件。

