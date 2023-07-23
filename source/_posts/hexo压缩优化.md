---
title: hexo压缩优化
date: 2019-05-30 08:14:08
tags:
  - hexo
---

使用 hexo-neat 压缩 html,css 和 js 文件

<!--more-->

## 安装

```bash
npm i -S hexo-neat
```

## 配置

添加以下代码到`_config.yml`

```yml
neat_enable: true
neat_html:
  exclude:
    - "**/*.md"
neat_css:
  exclude:
    - "**/*.min.css"
neat_js:
  exclude:
    - "**/*.min.js"
```

## 测试

使用`hexo g`，查看输出，如有 js 压缩错误  
参考以下配置跳过它们

```yml
neat_js:
  exclude:
    - "**/*.min.js"
    - "**/local-search.js"
    - "**/utils.js"
    - "**/next-boot.js"
    - "**/pisces.js"
```
