---
title: vscode设置中文php文档
tags: 随笔 vscode php
date: 2019-05-27 14:52:09
---
PHP Intelephense 中文提示
<!--more-->
1. 下载汉化包, [下载地址](https://github.com/fw6669998/php-doc/raw/master/document/out.zip)
2. 下载后解压缩, 得到一个`out`文件夹, 下面有许多子文件夹
3. 打开PowerShell, 输入下面的命令, 接着按下`tab`键, 然后`enter`回车
```powershell
explorer ~\.vscode\extensions\bmewburn.vscode-intelephense-client-*\node_modules\intelephense\lib
```
4. 将此目录下原先的`stub`文件夹备份或删除
5. 将`out`文件夹复制到此处, 并重命名为`stub`

汉化项目地址: https://github.com/fw6669998/php-doc
