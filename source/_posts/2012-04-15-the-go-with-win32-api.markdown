---
layout: post
title: "使用 Go 调用 Windows API"
date: 2012-04-15 10:23
type: post
published: true
comments: true
categories:
    - Technology
    - 我的声音
tags:
    - Go
    - Windows
---
Go 通过 [cgo](http://golang.org/cmd/cgo/) 可以利用现有C语言库

例如在 Windows 中使用 Go 调用 Win32 API

首先安装必要的工具

1. [Go](http://golang.org)
2. [MingW](http://mingw.org)

{% codeblock 项目文件完成后的布局 %}
%GOPATH%
    +- src
        +- w32api
            +- kernel.go
        +- testapp
            +- main.go
    +- bin # go install testapp
        +- testapp.exe
    +- pkg # go install w32api
        +- windows_386
    +- testapp.exe
{% endcodeblock %}

包装 Windows API
{% codeblock kernel.go lang:go %}
package w32api

// #define WIN32_LEAN_AND_MEAN
// #include <windows.h>
import "C"
import "syscall"

func GetCurrentDirectory() string {
    if bufLen := C.GetCurrentDirectoryW(0, nil); bufLen != 0 {
            buf := make([]uint16, bufLen)
            if bufLen := C.GetCurrentDirectoryW(bufLen, (*C.WCHAR)(&buf[0])); bufLen != 0 {
                        return syscall.UTF16ToString(buf)
            }
        }
    return ""
}
{% endcodeblock %}

*注意*：

在 import "C" 和 // #include <windows.h> 之间不能有空行

编译并安装

{% codeblock lang:bash %}
go build w32api
go install w32api
{% endcodeblock %}

调用

{% codeblock main.go %}
package main

import "w32api"

func main() {
    println(w32api.GetCurrentDirectory())
}
{% endcodeblock %}

{% codeblock lang:bash %}
go build testapp
go install testapp
{% endcodeblock %}

###Troubleshooting
* can't load package: package w32api: import "w32api": cannot find package

原因是没有设置环境变量 GOPATH

* exec gcc: exec: "gcc": executable file not found in %PATH%

原因是 gcc 所在目录没有加入道 %PATH% 中，检查 MingW 是否正确安装，并将 bin 目录加入到环境变量 %PATH% 中

###参考
[使用CGO封装Windows API](http://www.cnblogs.com/AllenDang/archive/2012/02/21/2361197.html)
