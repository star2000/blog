---
title: debian启动卡顿
date: 2019-04-15 10:38:00
tags:
  - linux
  - debian
---

debian 开机卡顿了将近两分钟时间

<!--more-->

在查看`dmesg`信息后发现，开机时卡在了`crng`收集熵，使用以下命令解决

```bash
apt install -y haveged
```
