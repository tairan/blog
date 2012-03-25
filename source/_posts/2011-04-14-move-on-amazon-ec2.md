---
layout: post
title: 转战亚马逊EC2
tags:
- AWS
- EC2
- Nginx
- Technology
- 实践手札
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
EC2 Nginx PHP FastCGI MySQL WordPress

关于 Amazon EC2 的教程已经铺天盖地了，有英文也有<a href="http://www.baidu.com.ru/archives/556.html">中文</a>。现在EC2对新注册的用户有优惠，及Micro Instance级别的会有1年的<a href="http://aws.amazon.com/free/">免费</a>份额。注意只是对新注册用户，如果你已经注册了 AWS 账户，即使并没有开通任何服务也不属于新注册用户，意思就是只要你使用就没有免费的。这一点我是用了$2美金的账单换来的教训。<a href="http://www.poemcode.net/2011/04/aws-free-usage-tier/">网上也有其他同学遇到</a>，看来不仔细阅读文档就是没文化的代表。这里是账单查询地址<a href="https://aws-portal.amazon.com/gp/aws/developer/account/index.html?ie=UTF8&action=activity-summary">https://aws-portal.amazon.com/gp/aws/developer/account/index.html?ie=UTF8&action=activity-summary</a> 一旦发现产生莫名其妙的费用，赶紧查。

我这次使用 Amazon EC2 的目的是把即将到期的博客迁移到这里，并且让手中的一些闲置域名也利用起来。其中还有一个更重要的目的就是为部署一个很重要的网站，基于Django的。

首先要做的是迁移博客。
进入 EC2 后需要安装一些软件，因为Micro Instance只能使用Amazon Linux(redhat系)，所以包管理器使用的是yum。
<pre lang="bash">
sudo yum install mysql mysql-libs mysql-server php php-mysql spawn-fcgi nginx
</pre>
启动MySQL后，并更改root用户的密码
<pre lang="bash">
sudo service mysqld start
/usr/bin/mysqladmin -u root -p -h localhost password 'newpassword'
</pre>
配置 Nginx， 在这里我遇到了一些问题，折腾了一天才搞定。这里要十分的感谢网友 <a href="http://www.douban.com/people/hfw_1987/">hfw_1984</a> 的帮助。遇到的问题主要集中在fastcgi部分，如果要让Nginx支持我博客的URL格式如http://www.tairan.net/index.php/2011/03/30/follow-the-right-way/ 则必须参照以下配置：
<pre lang="config">
    location ~ ^.+\.php {
        fastcgi_split_path_info ^(.+\.php)(/.+)$;  # 这一行必须放在 SCRIPT_FILENAME 上面，否则会被覆盖。
        fastcgi_param   SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        #fastcgi_param   PATH_INFO   $fastcgi_path_info; # 这两行并不需要
        #fastcgi_param   PATH_TRANSLATED $document_root$fastcgi_path_info;
        include /etc/nginx/fastcgi_params;
        fastcgi_pass 127.0.0.1:9000;
    }
</pre>
Micro Instance 默认提供的Nginx Version: 0.8.53

以上就是这两天的战果，还有其他的一些东西已经被写成自动化脚本，为方便备份数据，再次迁移、部署提供方便。

总的来说在墙内，使用EC2也不错，性价比不是最好，但是绝对值得试用。:-)
