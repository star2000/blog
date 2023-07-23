---
title: manjaro随笔
date: 2020-07-24 20:35:00
tags:
  - manjaro
  - linux
---

manjaro 随笔

<!--more-->

安装时选择`btrfs`文件系统可瞬间完成快照

1. 换最近的镜像源

```sh
sudo pacman-mirrors --geoip && sudo pacman -Syy
```

2. 添加 archlinuxcn 的清华镜像源

```sh
echo -e '[archlinuxcn]\nServer = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch' | sudo tee -a /etc/pacman.conf && sudo pacman -Sy --noconfirm archlinuxcn-keyring
```

3. 自动快照，然后升级系统(当系统发生故障时，运行`sudo timeshift --restore`并删除该软件包，直到问题解决)

```sh
pamac build --no-confirm autoupgrade
```

4. 提权免密(可选, 类似 windows 的 UAC 不弹窗)

```sh
pamac build --no-confirm nopasswd
```

5. 安装中文输入法(需要选中含有`简体中文`可选依赖, 注销或重启后生效)

```sh
pamac install --no-upgrade manjaro-asian-input-support-fcitx5
```

6. 修正配置 Noto Sans CJK 避免中文显示为异体（日文）字形

```sh
echo '<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <alias>
        <family>sans-serif</family>
        <prefer>
            <family>Noto Sans CJK SC</family>
        </prefer>
    </alias>
    <alias>
        <family>serif</family>
        <prefer>
            <family>Noto Serif CJK SC</family>
        </prefer>
    </alias>
    <alias>
        <family>monospace</family>
        <prefer>
            <family>Noto Sans Mono CJK SC</family>
        </prefer>
    </alias>
</fontconfig>' | sudo tee /etc/fonts/conf.d/64-language-selector-prefer.conf && fc-cache -fv
```

7. 更新并重启

```sh
pamac update --no-confirm && reboot
```
