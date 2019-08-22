---
title: hexo 自动部署 最小配置
tags: [随笔, hexo, 自动部署]
date: 2019-05-18 18:00:54
---
今天研究了下自动部署博客，  
在网上找到的教程中，  
配置都比较复杂，  
于是去官方文档寻找最优雅的配置。
<!--more-->

## 注册[travis]

![注册]

## 创建令牌

![项目令牌]

## 设置环境变量

![环境变量]

## 修改`_config.yml`

```yml
deploy:
  type: git
  name: 星
  email: i@star2000.work
  repo: https://TOKEN_USER:TOKEN_PWD@git.dev.tencent.com/xing2000/xing2000.coding.me
```

## 添加`.travis.yml`

```yml
language: node_js
node_js: node
git:
  depth: 1
cache: npm
install: npm i --production
before_script: sed -i "s/TOKEN_USER/${TOKEN_USER}/;s/TOKEN_PWD/${TOKEN_PWD}/" _config.yml
script: ./node_modules/.bin/hexo g -d
```

[travis]: https://travis-ci.org
[注册]: 注册.jpg
[项目令牌]: 项目令牌.jpg
[环境变量]: 环境变量.jpg
