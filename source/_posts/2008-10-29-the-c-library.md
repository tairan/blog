---
layout: post
title: The C Library
tags:
- library
- Technology
- The C Language
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
当我们学完C语言之后却发现不能用C语言写点什么东西。这种错觉严重的阻碍了大家在C语言道路上前进的步伐。和Java ，C# 一样C语言也有丰富的类库，而且都是经过了时间的考验。下面贴一些比较常用的开源C Library。

<strong>libc</strong>
<a href="http://www.gnu.org/software/libc/libc.html" target="_blank">Home Page
</a>

GNU C Library is one of the most important components of the GNU Hurd and most modern GNU/Linux distributions. It is used by almost all C programs and provides the most essential program interface.

<strong>Libstrfunc</strong>
<a href="http://sourceforge.net/project/showfiles.php?group_id=16501" target="_blank">Home Page</a>

Handy library for manipulating strings, string arrays, buffers, CGI forms, configuration files, textual templates, regular expressions, date/time parsing, et cetera. It handles base64, quoted-printable, url_encode, mime-words and other encoded data.

<strong>Libcurl</strong>
<a href="http://curl.haxx.se/libcurl/" target="_blank">Home Page</a>

'libcurl' client-side URL transfer library, supporting FTP, FTPS, HTTP, HTTPS, GOPHER, TELNET, DICT, FILE and LDAP. It also supports HTTPS certificates, HTTP POST, HTTP PUT, FTP uploading, kerberos, HTTP form based upload, proxies, cookies, user+password authentication, file transfer resume, and http proxy tunneling, and has bindings for 21 languages.

<strong>Libxml2</strong>
<a href="http://xmlsoft.org/" target="_blank">Home Page</a>

Libxml is the XML C library developed for the Gnome project. The library code is portable and modular; most of the extensions can be compiled out. Libxml implements a number of existing standards related to markup languages, including the XML standard, Namespaces in XML, XML Base, RFC 2396, XPath, XPointer, HTML4, XInclude, SGML Catalogs, and XML Catalogs.

In most cases, libxml tries to implement the specifications in a relatively strict way. To some extent, it provides support for the following specifications, but doesn't claim to implement them: DOM, FTP client, HTTP client, SAX, and DocBook SGML. Support for W3C XML Schemas is in progress.

<strong>netwib</strong>
<a href="http://www.laurentconstantin.com/en/netw/netwib/" target="_blank">Home Page</a>

Netwib is a network library for administrators and hackers. Its objective is to let programmers easily create network programs. This library provides features for Ethernet, IP, UDP, TCP, ICMP, ARP, and RARP protocols. It supports spoofing, sniffing, client, and server creation. Furthermore, netwib contains high level functions dealing with data handling.

This packages was formerly known as 'lcrzo.'

<strong>Apache Portable Runtime (APR) project</strong>
<a href="http://apr.apache.org/" target="_blank">Home Page</a>

The mission of the Apache Portable Runtime (APR) project is to create and maintain software libraries that provide a predictable and consistent interface to underlying platform-specific implementations.  The primary goal is to provide an API to which software developers may code and be assured of predictable if not identical behaviour regardless of the platform on which their software is built, relieving them of the need to code special-case conditions to work around or take advantage of platform-specific deficiencies or features.

btw: Subversion 就是使用 APR 作为底层库的
