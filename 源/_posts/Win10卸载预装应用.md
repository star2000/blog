---
title: Win10卸载预装应用
tags: 随笔
date: 2019-02-18 20:09:20
---
通常刚安装的Win10都自带了一些无用的商店应用，  
想卸载又不想一个个点，这里有方便的卸载命令。
<!--more-->
打开PowerShell，执行以下命令
```ps1
Get-AppPackage |% {if ($_.Name -ne 'Microsoft.WindowsStore') {Remove-AppPackage $_}}
```
将会出现大量警告，  
意思是拒绝卸载系统需要的应用，  
不必担心，应用商店不会被卸载，  
所有的应用都能从应用商店找到。