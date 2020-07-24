---
title: linux提权免密
date: 2019-03-21 15:30:44
tags:
  - linux
---

sudo，kdesu，Polkit 的单行提权命令

<!--more-->

`wheel`组提权免密

`arch`系可以安装`aur`中我写的`nopasswd`包

- sudo

```bash
echo '%wheel ALL=(ALL) NOPASSWD: ALL' | sudo tee -a /etc/sudoers
```

- kdesu

Octopi 免弹窗, 依赖`sudo`免密

```bash
kwriteconfig5 --file kdesurc --group super-user-command --key super-user-command sudo
```

- Polkit

系统设置免弹窗

```bash
echo 'polkit.addRule(function(action, subject) {if (subject.isInGroup("wheel")) {return polkit.Result.YES;}});' | sudo tee /etc/polkit-1/rules.d/49-nopasswd_global.rules
```
