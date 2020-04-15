---
title: 代理git协议
date: 2019-4-25 09:18:00
tags:
  - git
  - 代理
---

代理 git 协议，免询问密码

<!--more-->

{% tabs tabs %}

<!-- tab Windows -->

编辑`~/.ssh/config`文件，添加如下配置

```
Host github.com
    ProxyCommand connect -S 127.0.0.1:1080 -a none %h %p
```

<!-- endtab -->
<!-- tab Linux -->

安装`netcat`
{% tabs netcat %}

<!-- tab apt -->

```
sudo apt install -y netcat-openbsd
```

<!-- endtab -->
<!-- tab yum -->

```
sudo yum install -y netcat-openbsd
```

<!-- endtab -->
<!-- tab pacman -->

```
sudo pacman -Sy --noconfirm openbsd-netcat
```

<!-- endtab -->

{% endtabs %}

编辑`~/.ssh/config`文件，添加如下配置

```
Host github.com
   ProxyCommand nc -x 127.0.0.1:1080 %h %p
```

<!-- endtab -->

{% endtabs %}
