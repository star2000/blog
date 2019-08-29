---
title: 代理git协议
date: 2019-4-25 09:18:00
tags: 
  - git
  - 代理
---
代理git协议，免询问密码
<!--more-->
## 前提

如果是`linux`，需要`connect-proxy`包

```bash
apt install -y connect-proxy
```

## 配置

编辑`~/.ssh/config`文件，添加如下配置

```bash
Host github.com
    ProxyCommand connect -S 127.0.0.1:1080 -a none %h %p
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
