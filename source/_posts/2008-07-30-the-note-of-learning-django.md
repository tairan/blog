---
layout: post
title: The note of learning Django
tags:
- Django
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
  blogger_permalink: /2008/07/django-apache2.html
  _edit_last: '2'
  aktt_notify_twitter: 'no'
  _wp_old_slug: '26'
---
<h1>django 学习笔记</h1><h2>使用 apache2.2 + mod_python 部署django 项目</h2><br />#装载模块<br />LoadModules   python_module       modules/mod_python.so<br /><br />#声明虚拟主机<br />NameVirtualHost 127.0.0.1:80<br /><br />#定义虚拟主机<br />&lt;VirtualHost 127.0.0.1:80&gt;<br />&lt;Location /&gt;<br />    SetHandler python-program<br />    PythonHandler django.core.handlers.modpython<br />    SetEnv DJANGO_SETTINGS_MODULE mysite.settings         <br />    PythonDebug On<br />    PythonPath "['D:workspace'] + sys.path"<br />&lt;/Location&gt;<br />&lt;/VirtualHost&gt;<br /><br />SetEnv DJANGO_SETTINGS_MODULE mysite.settings<br />此处是django project的settings文件，根据python import 包的机制，这个和 PythonPath 息息相关。<br />假设django project目录是 d:workspacemysite，设置PythonPath时如果是d:workspace， 那么在设置django project的settings时就是 mysite.settings<br />如果设置PythonPath为d:workspacemysite ，那么只要指定 settings 即可，而不需要mysite的包名了。<br />此处还影响着 settings.py 文件中的 ROOT_URLCONF<br /><br />#TODO使用虚拟目录部署<br /><br /><h2>配置 Django project 中的静态资源 css js jpg 等</h2>通过阅读他人的源码，把这个问题也明白了。传说 Django 不建议在 settings 设置 MEIDA_ROOT 等相关静态文件配置。那么我们在模板中如何使用这些文件呢。如，在模板中我们使用 /media/css/layout.css ，web server怎么样才能知道这个路径在什么地方呢？<br />当然，Django中提供了相应的解决办法:通过url映射。在urls.py中做一下设置<br />urlpatterns += patterns('',<br />      (r'^media/(?P&lt;path&gt;.*)$', 'django.views.static.serve', {'document_root':'d:/templates/media'}),<br />)<br /><br />通过这样的映射，静态的资源的问题就解决了。:)<br /><br /><h1>Django URL dispatcher</h1>1. project 级别的 url 调用 app 级别的url<br /><br />此处要注意的是，project url + app url 才是真正的url，所以写url的正则表达式时，注意^ $两个符号<br /><br />2. 通过Url传递Get Request参数<br /><br />如果我们 detail(request, name) 的方法需要一个name参数，那么我们的正则表达式应该这样写 (r'^detail/P&lt;?name&gt;w+$', 'detail')<br /><br />3. 快捷调用 view<br />在appproject.views中有个index方法 在patterns 中第一个参数指定view后，在以后的调用只需指定方法名即可<br />urlpatterns = patterns('appproject.views',<br />      (r'^$', 'index'),<br />)<br />
