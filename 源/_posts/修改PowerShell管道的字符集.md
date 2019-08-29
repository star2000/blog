---
title: 修改PowerShell管道的字符集
date: 2019-05-12 09:39:27
tags:
  - powershell
---

当我使用PowerShell运行`'print("你好")' | py`时，输出两个问号  
<!--more-->
之所以这样，是因为PowerShell中的管道默认字符集是ASCII  
使用如下命令来临时更改管道的输出字符集

```powershell
$OutputEncoding=[Text.Encoding]::UTF8
```
