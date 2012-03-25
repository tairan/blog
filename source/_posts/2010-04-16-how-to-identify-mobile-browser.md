---
layout: post
title: 如何识别手机浏览器信息
tags:
- Browser
- Mobile
- PHP
- Technology
- 实践手札
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
---
想作一个网站，根据不同的访问者提供不同的显示模板，如适合手机的模板，适合PC浏览器的模板。

 从哪里识别访问者的信息，以及如何识别呢？

依据 HTTP 协议，客户端浏览网页的时候会提供一些信息给服务器端。下面是PC浏览器访问时的 <a href="http://cn.php.net/manual/en/reserved.variables.server.php" target="_blank">$_SERVER</a> 的 dump 信息。
<pre lang="PHP">
(array) Array
(
    [ALL_HTTP] => HTTP_CACHE_CONTROL:max-age=0
HTTP_CONNECTION:keep-alive
HTTP_CONTENT_LENGTH:0
HTTP_ACCEPT:application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
HTTP_ACCEPT_CHARSET:ISO-8859-1,utf-8;q=0.7,*;q=0.3
HTTP_ACCEPT_ENCODING:gzip,deflate,sdch
HTTP_ACCEPT_LANGUAGE:en-US,en;q=0.8
HTTP_COOKIE:__utmz=259664206.1262318873.1.1.utmcsr=google|utmccn=(organic)|utmcmd=organic|utmctr=51xna; __utma=259664206.724256099.1262318873.1262318873.1262318873.1
HTTP_HOST:www.51xna.com
HTTP_USER_AGENT:Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/533.2 (KHTML, like Gecko) Chrome/5.0.342.9 Safari/533.2

    [HTTPS] => off
    [SCRIPT_NAME] => /private/Kohana/index.php
    [HTTP_COOKIE] => __utmz=259664206.1262318873.1.1.utmcsr=google|utmccn=(organic)|utmcmd=organic|utmctr=51xna; __utma=259664206.724256099.1262318873.1262318873.1262318873.1
    [AUTH_PASSWORD] => 
    [AUTH_TYPE] => 
    [AUTH_USER] => 
    [CONTENT_LENGTH] => 0
    [CONTENT_TYPE] => 
    [PATH_TRANSLATED] => g:\wwwroot\51xna.com\wwwroot\mobile\index
    [QUERY_STRING] => 
    [REMOTE_ADDR] => 221.227.130.23
    [REMOTE_HOST] => 221.227.130.23
    [REMOTE_USER] => 
    [REQUEST_METHOD] => GET
    [SERVER_NAME] => www.51xna.com
    [SERVER_PORT] => 80
    [SERVER_PROTOCOL] => HTTP/1.1
    [SERVER_SOFTWARE] => Microsoft-IIS/6.0
    [APPL_MD_PATH] => /LM/w3svc/798/ROOT
    [APPL_PHYSICAL_PATH] => g:\wwwroot\51xna.com\wwwroot\
    [INSTANCE_ID] => 798
    [INSTANCE_META_PATH] => /LM/W3SVC/798
    [LOGON_USER] => 
    [REQUEST_URI] => /private/Kohana/index.php/mobile/index
    [URL] => /private/Kohana/index.php/mobile/index
    [SCRIPT_FILENAME] => g:\wwwroot\51xna.com\wwwroot\private\Kohana\index.php
    [ORIG_PATH_INFO] => /private/Kohana/index.php/mobile/index
    [PATH_INFO] => /mobile/index
    [ORIG_PATH_TRANSLATED] => g:\wwwroot\51xna.com\wwwroot\private\Kohana\index.php\mobile\index
    [DOCUMENT_ROOT] => g:\wwwroot\51xna.com\wwwroot
    [PHP_SELF] => /private/Kohana/index.php
    [HTTP_CACHE_CONTROL] => max-age=0
    [HTTP_CONNECTION] => keep-alive
    [HTTP_CONTENT_LENGTH] => 0
    [HTTP_ACCEPT] => application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
    [HTTP_ACCEPT_CHARSET] => ISO-8859-1,utf-8;q=0.7,*;q=0.3
    [HTTP_ACCEPT_ENCODING] => gzip,deflate,sdch
    [HTTP_ACCEPT_LANGUAGE] => en-US,en;q=0.8
    [HTTP_HOST] => www.51xna.com
    [HTTP_USER_AGENT] => Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/533.2 (KHTML, like Gecko) Chrome/5.0.342.9 Safari/533.2
    [REQUEST_TIME] => 1271408243
    [argv] => Array
        (
        )

    [argc] => 0
)
</pre>

通常我们可以在HTTP_USER_AGENT中找到识别信息，其中PC浏览器的HTTP_USER_AGENT信息最全，很容易根据关键字来识别如'Chrome', 'Firefox' 等，部分手机浏览器也可以可以通过 'Windows Mobile', 'Windows Phone', 'SymbianOS', 'Nokia', 'Opera Mobi', 'Android'等关键字识别，这里有一个手机HTTP_USER_AGENT识别列表<a href="http://www.zytrax.com/tech/web/mobile_ids.html" target="_blank">http://www.zytrax.com/tech/web/mobile_ids.html</a>。但是有些手机上的浏览器并不提供HTTP_USER_AGENT信息。

如今的智能手机大多都支持 XHTML 格式浏览，我们可以通过 HTTP_ACCEPT 来识别手机是否支持 XHTML 格式浏览。这里识别的关键字主要是 'application/xhtml+xml'。

另外还有一种识别方式，通过查找用户的上网方式，通常手机用户走的是 GPRS 路线，但是这中识别方式并不可靠，可以作为一种辅助识别手段。

对于只支持 WML 的手机目前我还没有解决，一些非智能手机在访问网站时会提示"不支持所访问的网站"。开始我以为是返回信息的问题，当我把返回信息严格按照WML格式输出时问题依然存在。不知道这种手机是通过什么方式访问互联网的。

为所有用户提供不同的定制服务是一件不可能的完成任务，支持大多数就好。完美主义总是很浪费时间。

最后感谢各位提供手机访问信息的童鞋们，让你们忍受在手机上输入如此之长的URL，实在辛苦！
