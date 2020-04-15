---
title: Win10卸载预装应用
date: 2019-02-18 20:09:20
tags:
  - windows
---

通常刚安装的 Win10 都自带了一些无用的商店应用，  
而且有些还没有卸载按钮，  
想卸载又不想一个个点，这里有方便的卸载命令。

<!--more-->

按`Win+R`执行以下命令

```powershell
powershell Get-AppPackage|?{ $_.Name -ne 'Microsoft.WindowsStore'}|Remove-AppPackage -ea Ignore
```
