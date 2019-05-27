---
title: aria2自启动
tags: 随笔 aria2
date: 2019-04-18 16:37:00
---
aria2 是个轻量级的多线程下载器，能轻松跑满网速，极速下载。  
但它自身不带图形化界面，这里是我的配置
<!--more-->
1. [下载aria2](https://github.com/aria2/aria2/releases/latest)
2. 将压缩包里的`aria2c.exe`复制到`C:\Windows`目录下
3. 打开记事本，复制下面的代码
```vb
CreateObject("WScript.Shell").Run "aria2c --enable-rpc -d%USERPROFILE%\Downloads -k1M -x16 -c -s1024",0
```
4. `Ctrl+S`保存时，在地址栏输入`shell:startup`，文件名输入`aria2.vbs`即可
5. 安装面板插件[Aria2 for Chrome](https://chrome.google.com/webstore/detail/aria2-for-chrome/mpkodccbngfoacfalldjimigbofkhgjn)
6. 右键插件图标，点击选项，将`JSON-RPC`后第二个空，改为`http://127.0.0.1:6800/jsonrpc`，点击绿色的保存按钮，这里推荐勾选自动拦截