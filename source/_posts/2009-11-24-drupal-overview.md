---
layout: post
title: 近距离Drupal概览
tags:
- Drupal
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
面对国内用户，中文是必须的，因此需要安装中文语言包，目前6.x版本的中文语言包做的不错，下载后直接解压到drupal文件根目录即可。我是在使用drupal安装脚本配置之前就将中文语言包放到drupal所在的文件目录的，这样开始使用drupal安装脚本配置的时候会提示配置中文的。

Drupal 支持主题(Theme)和模块插件(Module)，如此一来给网站换马甲和增加武器装备就变得容易。

如果你浏览了Drupal的主题和模块下载页面，你一定会惊讶主题和模块的种类是如此的多。挑一个喜欢的，实用的下载后分别解压到 drupal/sites/all/{theme,modules}目录下，如果这两个目录没有先创建。把主题和模块放在这里是推荐设置，顾名思义，这是对所有site生效的设置（Drupal支持同一程序下多个站点）。当然如果非要放到Drupal核心模块和主题那里也是可以的，只是不推荐而已。

在确定网站需要的功能后先到module下载页找找，实在没有的话就自己写，如果自己写的还有其他人需要的，再反馈给drupal社区，良性循环！

这是我对Drupal的第一次仔细观察的印象，之前也安装了几次，一直就没仔细瞧过，惭愧。

参考：
<ul>
	<li><a href="http://drupal.org/project/Translations" target="_blank">Drupal 语言包</a></li>
	<li><a href="http://drupal.org/project/Themes" target="_blank">Drupal 主题</a></li>
	<li><a href="http://drupal.org/project/Modules" target="_blank">Drupal 模块</a></li>
</ul>
EOF
