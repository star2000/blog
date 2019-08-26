---
title: linux鉴权免密
tags: [随笔, linux]
date: 2019-03-21 15:30:44
---
sudo, kdesu, Polkit 的单行提权命令
<!--more-->
- sudo

```bash
echo '%wheel ALL=(ALL) NOPASSWD: ALL' | sudo tee -a /etc/sudoers
```

- kdesu

Octopi 免弹窗

```bash
kwriteconfig5 --file kdesurc --group super-user-command --key super-user-command sudo
```

- Polkit

系统设置免弹窗

```bash
echo 'polkit.addRule(function(action, subject) {if (subject.isInGroup("wheel")) {return polkit.Result.YES;}});' | sudo tee /etc/polkit-1/rules.d/49-nopasswd_global.rules
```
