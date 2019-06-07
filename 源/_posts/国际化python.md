---
title: 国际化python
tags: [项目, python]
date: 2019-05-11 23:08:52
---
为python自身添加多语言支持  
<!--more-->
# [项目地址](https://github.com/star2000/i18n-python)  
最初的想法是用vscode写代码时，不用看那些英文提示。  
安装好后，你会发现`help()`的输出变成了中文。  
vscode的提示也会变成中文。

# 安装
- Windows:
```powershell
$OutputEncoding=[Text.Encoding]::UTF8;(wget 'https://github.com/star2000/i18n-python/raw/master/scripts/install.py').Content | py
```
- Linux:
```bash
wget -qO- 'https://github.com/star2000/i18n-python/raw/master/scripts/install.py' | python3
```

# 测试

- Windows: 
```powershell
py -m pydoc print
```
- Linux: 
```bash
pydoc3 print
```

# 注意

- 安装速度取决于你连接github的网速，一般国内需要一两分钟，文件大概有3M大小
- 我使用机器翻译，水平大家都知道，欢迎来修正翻译
- 此项目受以下环境变量影响：`LANGUAGE`, `LC_ALL`, `LC_MESSAGES`, `LANG` ，优先级依次递增，Windows上默认使用系统语言

# 卸载
- Windows:
```powershell
$OutputEncoding=[Text.Encoding]::UTF8;(wget 'https://github.com/star2000/i18n-python/raw/master/scripts/uninstall.py').Content | py
```
- Linux:
```bash
wget -qO- 'https://github.com/star2000/i18n-python/raw/master/scripts/uninstall.py' | python3
```

# [参与翻译](https://crowdin.com/project/i18n-python)
