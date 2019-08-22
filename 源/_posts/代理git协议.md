---
title: 代理git协议
tags: [git, 代理]
date: 2019-4-25 09:18:00
---
网上的方法要么配置麻烦，要么有缺陷，所以这里有一行脚本
<!--more-->
## Windows上

打开PowerShell，执行以下命令

```ps1
New-Item -Path ~\.ssh\config -Value "Host github.com`n    ProxyCommand connect -S 127.0.0.1:1080 -a none %h %p" -Force
```

## Linux上

打开终端，执行以下命令

```sh
mkdir ~/.ssh;apt install -y connect-proxy && echo -e 'Host github.com\n    ProxyCommand connect -S 127.0.0.1:1080 -a none %h %p' > ~/.ssh/config
```

## 名词解释

| 名词         | 解释                                                     |
| ------------ | -------------------------------------------------------- |
| Host         | 匹配主机                                                 |
| ProxyCommand | 代理命令                                                 |
| connect      | mingw64自带的代理命令                                    |
| -S           | 指定socks代理，默认socks5                                |
| -a           | 指定身份验证方法，不指定为none的话，会弹出输入密码的提示 |
| %h           | 将被替换为主机                                           |
| %p           | 将被替换为端口                                           |
