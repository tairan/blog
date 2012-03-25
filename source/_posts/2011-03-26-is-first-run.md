---
layout: post
title: 如何判断程序是安装后第一次执行
tags:
- .NET
- Microsoft
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
  _wp_old_slug: ! '%e5%a6%82%e4%bd%95%e5%88%a4%e6%96%ad%e7%a8%8b%e5%ba%8f%e6%98%af%e5%ae%89%e8%a3%85%e5%90%8e%e7%ac%ac%e4%b8%80%e6%ac%a1%e6%89%a7%e8%a1%8c'
---
有时我们需要在程序第一次启动的时候进行一些初始化工作，如何识别程序是部署后第一次运行呢？ .net framework就提供了这样的功能。

参考这里 <a href="http://msdn.microsoft.com/zh-cn/library/system.deployment.application.applicationdeployment.isfirstrun.aspx">http://msdn.microsoft.com/zh-cn/library/system.deployment.application.applicationdeployment.isfirstrun.aspx </a>

这里还有更多的关于.net 程序部署相关的技术说明 。<a href="http://msdn.microsoft.com/zh-cn/library/system.deployment.application.aspx">http://msdn.microsoft.com/zh-cn/library/system.deployment.application.aspx</a>
