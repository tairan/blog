---
layout: post
title: 我学习Kohana的方法
tags:
- Kohana
- PHP
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
Kohana 是一个PHP的开放框架，所以在学习之前需要深入了解PHP。另外Kohana也是一个遵循MVC模式的开发框架，同样在学习之前还需要深入了解什么是MVC，最好动手写过MVC模式的页面，一个练习也行。

接下来我们从那里开始呢？

在动手练习之前，需要阅读文档。先哲说：闲时读手册，忙时问Google。刚开始我们有充裕的时间，那么开始阅读文档吧。

作为入门，属于<strong>Getting Started</strong>的文档需要优先阅读。通过阅读<a href="http://kohanaframework.org/guide/about.kohana" target="_blank">What is Kohana?</a>，来了解下Kohana都有哪些东西。而 <a href="http://kohanaframework.org/guide/about.mvc" target="_blank">Model View Controller</a>则告诉你Kohana使用了一种改良型的MVC模式。接下来 <a href="http://kohanaframework.org/guide/about.filesystem" target="_blank">Cascading Filesystem</a> 告诉你这个改良型的MVC模式是怎么工作的。最后通过阅读<a href="http://kohanaframework.org/guide/about.flow" target="_blank">Request Flow</a>来了解从浏览器发出请求后Kohana在服务器端是怎么处理的。okay，通过阅读以上的文档就入门了。

阳明先生说，知是行之始，行是知之果，知行功夫不可离。意思是光看文档并不代表你知道，需要动手操练一番才算真知道。

Kohana安装还是很容易的，将整个工程放到web服务器上就可以工作了。如果遇到问题跑不起来怎么办？Fix it! 安迪教授也说了，当你在工作过程中没有得到想要的东西时你就获得了经验。

程序员动手的第一招是"Hello World"，Kohana已经提供了这一招，所以通过阅读源码来学习这一招是如何发出的，因为Kohana是改良的MVC(也就是HMVC)，那么需要多注意项目的目录结构，看看这些源文件是以什么样的方式组织的。在观摩Kohana提供的入门招数后，让我们来破解这个招式。尝试着修改文件名，类名，以及改变文件目录位置等来验证这一招在什么情况下会失效，这对你加深理解有帮助。

入门招数，学了也拆了，开始模拟演练吧。

新手入门第一课，留言板。很多前辈都推荐新手来实现一个留言板用以学习新的开发环境。动手之前，我们要有个蓝图，不用大，将期望了解的知识点囊括进去即可。web开发的知识点通常有，Session,Cookie的管理，数据库的操作，URL的管理，Ajax，表单验证，异常处理等。限定已经有了，那么就开始来实现留言板吧。

演练开始我们就忙了起来，这时Google就发挥作用了，遇到疑难杂症问Google。作为修炼内力，阅读<a href="http://kohanaframework.org/guide/api">API</a>加深理解各个类是如何工作。

最后，先哲也说了，尽信书不如无书。文档也有bug，当实际操作和文档描述的行为不相符的时候，那么我们就要玩外科手术了。这就是开源的好处，有bug直接解剖，肚皮划开后一目了然！
