---
layout: post
title: crontab增删命令
date: 2019-08-31 20:27:22
tags:
  - linux
  - crontab
---

更简单的在脚本中使用 crontab

<!--more-->

## 添加

```bash
crontab -l | sed '1i\0 0 * * * reboot' | crontab
```

## 删除

```bash
crontab -l | sed /reboot/d | crontab
```
