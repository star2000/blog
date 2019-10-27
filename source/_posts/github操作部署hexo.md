---
title: github操作部署hexo
date: 2019-08-29 09:06:07
tags:
  - hexo
  - 自动部署
---
使用[github操作]自动部署[hexo]博客
<!--more-->
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

## 添加`.github/workflows/main.yml`

```yml
on:
  - push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: 检出代码
        uses: actions/checkout@master
        with:
          fetch-depth: 1

      - name: 安装nodejs
        uses: actions/setup-node@master
        with:
          node-version: "*"

      - name: 安装依赖
        run: npm i --production

      - name: 安装主题
        run: git clone https://github.com/theme-next/hexo-theme-next themes/next --depth 1

      - name: 环境变量
        env:
          TOKEN_USER: ${{ secrets.TOKEN_USER }}
          TOKEN_PWD: ${{ secrets.TOKEN_PWD }}
        run: sed -i "s/TOKEN_USER/${TOKEN_USER}/;s/TOKEN_PWD/${TOKEN_PWD}/" _config.yml

      - name: 部署
        run: ./node_modules/.bin/hexo g -d
```

[github操作]: https://help.github.com/cn/articles/workflow-syntax-for-github-actions
[hexo]: https://hexo.io
[项目令牌]: 项目令牌.jpg
[环境变量]: 环境变量.jpg
