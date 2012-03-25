---
layout: post
title: 记阿里软件开放平台－－淘宝API
tags:
- taobao
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _searchme: '1'
  blogger_blog: hackersstory.blogspot.com
  blogger_author: Hacker Wanghttp://www.blogger.com/profile/09490459533264275905noreply@blogger.com
  blogger_permalink: /2008/09/api.html
  aktt_notify_twitter: 'no'
  _edit_last: '2'
---
现在很多的internet站点都开放了API，吸引广大的程序员和有眼光的商人利用host站点的资源来进行扩展开发。这样会带来不少的好处。<br />1. host提供者可以免费的获取广大的资源(有技术能力的人)来为他扩展系统，从而提高host用户的粘度，并且host并需要为此负担更多的风险，还可以更便捷的收购！<br />2. 寻找更好的创意。俗话说三个臭皮匠顶个诸葛亮，何况隐藏在"民间“的程序/创意高手不计其数！<br />3. 让草根更容易赚到第一桶金。创业的成本是跟高的，host提供API并共享了庞大的用户群，让一些有能力的个人或小公司得以付出比较少的成本就能将技术转化成生产力！<br /><br />基于以上和更多的诱惑，淘宝网也开放了自己的API。<br /><br />这个中秋节有一半的时间在倒腾这个淘宝的API。<br />首先，阅读文档，这是入门的不二之选。我认为淘宝的文档实在太少，而且文档的发布也不怎么正规。随便找个不不知道是什么身份的人在淘宝的论坛里发个帖子就算是文档的发布了。文档中的示例代码残缺不全，以前看ThinkPHP文档的时候也是这个感觉。<br /><br />阅读文档之后，实现一个demo。我选择的是淘宝的web版本的API，API调用的方式为REST。另外我需要一个虚拟主机用来托管程序，这里我选择了google的 app engine。所以python也就成了我的主要开发语言。<br /><br />在淘宝的文档中介绍了.net,java, php 的示例代码。我选择python来实现其实也并不困难。东西准备的差不多了，我们开始实验下吧。在众多杂乱无章的文档中，我看到了些说明。在开发之前要验证一下淘宝API的有效性。如调用 http://sipdev.alisoft.com/sip/rest?sip_apiname=alisoft.validateUser 则会返回xml格式的数据。内容大致是需要appkey。 就这个URL我折腾了好久阿。win+ie, win+firefox, linux+firefox 几个平台我都尝试访问，可是返回的却始终是ContentLength＝0的东西！而淘宝生产环境的API，http://sipd.alisoft.com/sip/rest?sip_apiname=alisoft.validateUser倒是能时不时的返回几个文档中说的结果。<br /><br />至此只好用淘宝生产环境的API来开发了。<br /><br />使用淘宝API需要生成一个MD5的签名用来认证。生成签名的步骤是，将code，appkey,appname等属性以及其值拼接成一个字符串后用MD5生成一个32位的字符串。我们都知道MD5签名时，内容有任何细微的差别生成的code都不一样。所以拼接这个字符串一定要小心小心再小心，不要多，不要少，注意区分大小写。<br /><br />生成签名后就是通过REST来调用API了。<br /><br />完整使用淘宝API还需要作很多工作，虽然文档比较烂，但总比没有的好。多看看，兴许能捡到什么有用的信息。<br /><br />BTW：我的第一个淘宝认证API调用失败了，最后的erro是签名不正确。如果谁热心愿意帮助我一下，我把代码发过去帮我review一下！谢谢！
