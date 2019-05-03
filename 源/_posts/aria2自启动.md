---
title: aria2自启动
tags: 随笔
date: 2019-04-18 16:37:00
---

1.[下载aria2](https://github.com/aria2/aria2/releases/latest)
2.将压缩包里的`aria2c.exe`复制到`C:\Windows`目录下
3.打开记事本
4.复制下面的代码
<!--more-->
```sh
CreateObject("WScript.Shell").Run "aria2c --enable-rpc -d%USERPROFILE%\Downloads -k1M -x16 -c -s1024",0
```
5.`Ctrl+S`保存时，在地址栏输入`shell:startup`，文件名输入`aria2.vbs`即可
