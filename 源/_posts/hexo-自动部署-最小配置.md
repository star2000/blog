---
title: hexo 自动部署 最小配置
tags: 随笔
date: 2019-05-18 18:00:54
---
# [travis]的最小配置
<!--more-->
今天研究了下自动部署博客，  
在网上找到的教程中，  
配置都比较复杂，  
于是去官方文档寻找最优雅的配置。

1. 注册[travis]
![注册]
2. 创建令牌
![项目令牌]
3. 设置环境变量
![环境变量]
4. 修改`_config.yml`
```yml
deploy:
  type: git
  name: 星
  email: i@star2000.work
  repo: https://TOKEN_USER:TOKEN_PWD@git.dev.tencent.com/xing2000/xing2000.coding.me
```
5. 添加`.travis.yml`
```yml
language: node_js
node_js: node
git:
  depth: 1
cache: npm
install: npm i
before_script: sed -i "s/TOKEN_USER/${TOKEN_USER}/;s/TOKEN_PWD/${TOKEN_PWD}/" _config.yml
script: ./node_modules/.bin/hexo g -d
```

[travis]: https://travis-ci.org
[注册]: /图片/注册.jpg
[项目令牌]: /图片/项目令牌.jpg
[环境变量]: /图片/环境变量.jpg