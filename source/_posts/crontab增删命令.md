---
layout: post
title: crontab增删命令
date: 2019-08-31 20:27:22
tags:
  - linux
  - crontab
  - shell
---

更简单的在脚本中使用 crontab

<!--more-->

## 添加

```bash
(crontab -l 2>/dev/null;echo '0 0 * * * reboot') | crontab -
```

## 删除

```bash
crontab -l 2>/dev/null | sed '/reboot/d' | crontab -
```
