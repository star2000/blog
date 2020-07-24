---
title: manjaro随笔
date: 2020-07-24 20:35:00
tags:
  - manjaro
  - linux
---

manjaro 随笔

<!--more-->

1. 换最近的镜像源

```bash
sudo pacman-mirrors --geoip
```

2. 提权免密(可选, 类似 windows 的 UAC 不弹窗)

```
pamac build --no-confirm nopasswd
```

3. 安装中文输入法(需要选中含有`简体中文`可选依赖, 注销或重启后生效)

```bash
pamac install manjaro-asian-input-support-fcitx5
```

4. 添加 archlinuxcn 源

```bash
echo -e '[archlinuxcn]\nServer = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch' | sudo tee -a /etc/pacman.conf && sudo pacman -Sy --noconfirm archlinuxcn-keyring
```

5. 自动快照，然后升级系统(当系统发生故障时，运行`sudo timeshift --restore`并删除该软件包，直到问题解决)

```bash
pamac build --no-confirm autoupgrade
```
