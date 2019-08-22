---
title: hexo压缩优化
tags: 随笔
date: 2019-05-30 08:14:08
---
使用hexo-neat压缩html,css和js文件
<!--more-->
## 安装

```sh
npm i -S hexo-neat
```

## 配置

添加以下代码到`_config.yml`

```yml
neat_enable: true
neat_html:
  exclude:
    - '**/*.md'
neat_css:
  exclude:
    - '**/*.min.css'
neat_js:
  exclude:
    - '**/*.min.js'
```

## 测试

使用`hexo s`运行本地服务,  
按`f12`查看控制台, 有无js文件加载错误  
我的博客中`/lib/jquery/index.js`脚本加载错误  
按以下配置排除它

```yml
neat_js:
  exclude:
    - '**/*.min.js'
    - '**/jquery/index.js'
```
