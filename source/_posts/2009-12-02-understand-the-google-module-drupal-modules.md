---
layout: post
title: 理解Drupal模块之Google
tags:
- Adsense
- Analytics
- Drupal
- Google
- sitemap
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
Google 是居家旅行、工作学习必备之搜索引擎，而且Google还可以给我们的网站带来收入。请看我细细道来：

Google的爬虫自不用说，不知道哪天就过来爬了你的网站，可这太依赖于运气，我们需要主动一点，向Google提交我们的网站信息帮助Google更好的索引我们的网站内容(?_? 咋就那么心甘情愿的交给Google呢)。同样Google为了方便我们提交资料，搞了个叫Sitemap的东西作为所有提交资料的规范格式。如此一说，我们对Drupal相关模块需求就了解了，我们需要一个能自动生成网站Sitemap的模块来供Google爬虫享用。

在Drupal模块页搜索"sitemap"， 首先映入眼帘的就是我们需要的那个啦 :-) 。下载、上传、启用模块不用罗嗦。Drupal Sitemap　模块中有５个功能，其中　Sitemap　是核心功能，必须滴！剩下的在仔细阅读说明后酌情启用！在<a href="http://www.51xna.com/" target="_blank">51xna.com</a>我启用了　XML sitemap engines　和　XML sitemap node　两个功能。这两个功能的用法还是蛮简单的，仔细阅读说明即可。

我们网站的资料都交给Google了，那么怎么知道网站都有哪些人来访问呢？这个问题Google也有解决方案，Google Analytics，顾名思义就是用来分析网站访问者的，如访问者的来源地、使用的浏览器、操作系统、访问页面、停留时间等等。

Drupal也有相关的模块来满足我们的这个需要，再次到Drupal模块页搜索“Analytics”，然后。。。（省略若干苦力活）在设置页面填上Google Analytics的帐号即可，其他的设置仔细阅读说明酌情操作。

最后，我们要从Google那里弄点米米养小站了。题外话，你该不是真的以为Google就是一个搜索引擎吧？其实Google是一广告机器，详细点说Google是一个跟广告有关的赚钱机器。Google Adsense 就是这部机器的关键部件之一。我们在Google Adsense上申请个账户，然后在自己的网站上提供广告位，然后Google利用你提供的广告位放广告，如果有人点击这些广告位上的广告，Google就按照专门的计算方式来给你分成，注意啦，分的是$美元。所以弄个Adsense的模块放在网站上是有必要的。

Drupal那里也有Google Adsense的相关模块（真的是要什么有什么:-)）

Adsense模块的功能还挺多，有7个。AdSense core 这个是核心模块必须启用，Managed ads 管理广告滴，负责显示广告区块的后面详述，其他的功能带 old 的说明是不推荐使用的。

进入到 首页 › 管理 › 站点设置 › AdSense 有一个Publish ID，这是用来输入Google Adsense帐号的，必须滴！现在用 Managed ads 来管理广告啦。在 首页 › 管理 › 站点设置 › AdSense 中设置 Adsense Blocks，这里输入一个正整数，用来表示你准备在页面上放多少个广告位的，先设置一个练练手。这时在 首页 › 管理 › 站点构建 › 区块 中就可以看到一个AdSense: unconfigured 0 的待设置的区块，在配置选项中配置好相应的设置以后，把这个区块放到某个地方，保存收工！

现在网站就变成了自动提交资料到Google等搜索引擎、可分析网站访问信息、以及放置广告位收费半赚钱的机器了，那一半呢？当然是网站内容和用户来贡献的咯！

最后来句广告：<a href="http://www.tairan.net/">tairan.net</a>也放置了Google Adsense广告位！

EOF
