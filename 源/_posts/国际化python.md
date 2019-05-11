---
title: 国际化python
tags: 随笔
date: 2019-05-11 23:08:52
---

# i18n-python
为python自身添加多语言支持  
<!--more-->
最初的想法是用vscode写代码时，不用看那些英文提示。  
安装好后，你会发现vscode的提示变成了中文。

# 安装
- Windows:
```sh
(wget 'https://raw.githubusercontent.com/star2000/i18n-python/master/bin/install.py').Content | py
```
- Linux:
```sh
wget -O- 'https://raw.githubusercontent.com/star2000/i18n-python/master/bin/install.py' | python3
```

# 测试

- Windows: 
```sh
py -m pydoc print
```
- Linux: 
```sh
pydoc3 print
```

# 注意

- 安装速度取决于你连接github的网速，一般国内需要一两分钟，文件大概有1M大小
- 我使用机器翻译，水平大家都知道，欢迎来修正翻译
- Windows的安装命令执行起来显示乱码，因为PowerShell中会把它转换为UTF16，我还没找到解决方法，如一段时间后，此问题还没解决，将会把执行提示改为英文
- 此项目受以下环境变量影响：`LANGUAGE`, `LC_ALL`, `LC_MESSAGES`, `LANG` ，优先级依次递增

# 卸载
- Windows:
```sh
(wget 'https://raw.githubusercontent.com/star2000/i18n-python/master/bin/uninstall.py').Content | py
```
- Linux:
```sh
wget -O- 'https://raw.githubusercontent.com/star2000/i18n-python/master/bin/uninstall.py' | python3
```

# 贡献

1. fork项目
2. 改进po文件夹下面的翻译文件
3. 提交pull-request

或者你想创建新的语言翻译  
那么你需要运行`bash bin/create-po.sh`  
它会读取你当前的语言环境，在po文件夹下创建
