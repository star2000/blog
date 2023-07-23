---
title: vscode设置中文php文档
date: 2019-05-27 14:52:09
tags:
  - vscode
  - php
---

PHP Intelephense 中文帮助

<!--more-->

## 下载

[汉化包地址](https://github.com/fw6669998/php-doc/raw/master/document/out.zip)

下载后解压缩，得到一个`out`文件夹，下面有许多子文件夹

## 配置

打开`PowerShell`，输入下面的命令，接着按下`tab`键补全，然后`enter`回车打开文件浏览器

```powershell
explorer ~\.vscode\extensions\bmewburn.vscode-intelephense-client-*\node_modules\intelephense\lib
```

将此目录下原先的`stub`文件夹备份或删除  
将`out`文件夹复制到此处，并重命名为`stub`

汉化项目地址: <https://github.com/fw6669998/php-doc>
