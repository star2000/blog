---
title: aria2配置
date: 2019-04-18 16:37:00
tags: 
  - aria2
---
aria2 是个轻量级的多线程下载器，能轻松跑满网速，极速下载。  
但它自身不带图形化界面，这里是我的配置
<!--more-->
## 后台

### [下载aria2]

![版本](版本.png)
将压缩包里的`aria2c.exe`复制到`C:\Windows`目录下

### 开机后台自启

复制下面的代码，`Win+R`粘贴后按`Enter`回车

```bat
cmd /c echo CreateObject("WScript.Shell").Run "aria2c --enable-rpc --rpc-allow-origin-all -d%USERPROFILE%\Downloads -k1M -x16 -c -s1024",0 > "%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup\aria2.vbs"
```

同样的步骤执行以下代码，立即启动后台

```bat
"%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup\aria2.vbs"
```

## 前台

以下任一方法皆可

### [Chrome插件]

- 点击[AriaNg设置](chrome-extension://mpkodccbngfoacfalldjimigbofkhgjn/ui/ariang/index.html#!/settings/ariang)，把地址改为`127.0.0.1`
![配置](配置.png)
- 右击[选项](chrome-extension://mpkodccbngfoacfalldjimigbofkhgjn/options.html)，勾选 `自动拦截下载任务到Aria2c`
![配置](配置2.png)

### [在线AriaNg界面]

- 点击[AriaNg设置](http://ariang.mayswind.net/latest/#!/settings/ariang)，把地址改为`127.0.0.1`
![配置](配置.png)

### [在线简单界面]

- 无需配置

[下载aria2]: https://github.com/aria2/aria2/releases/latest
[Chrome插件]: https://chrome.google.com/webstore/detail/aria2-for-chrome/mpkodccbngfoacfalldjimigbofkhgjn
[在线AriaNg界面]: http://ariang.mayswind.net/latest
[在线简单界面]: http://aria2c.com
