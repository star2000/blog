---
title: 代理git协议
tags: 随笔
date: 2019-4-25 09:18:00
---
# windows上
1. 创建~\\.ssh文件夹
`mkdir ~\.ssh`
2. 编写配置
`notepad ~\.ssh\config`
3. 写入以下内容
<!--more-->
```sh
Host github.com
    ProxyCommand connect -S 127.0.0.1:1080 -a none %h %p
```

# linux上
1. 安装connect命令
`apt install connect-proxy`
2. 创建~/.ssh文件夹
`mkdir ~/.ssh`
3. 编写配置
`vim ~/.ssh/config`
3. 写入以下内容
```sh
Host github.com
    ProxyCommand connect -S 127.0.0.1:1080 -a none %h %p
```

# 名词解释

名词         | 解释
-            | -
Host         | 匹配主机
ProxyCommand | 代理命令
connect      | mingw64自带的代理命令
-S           | 指定socks代理，默认socks5
-a           | 指定身份验证方法，不指定为none的话，会弹出输入密码的提示
%h           | 将被替换为主机
%p           | 将被替换为端口
