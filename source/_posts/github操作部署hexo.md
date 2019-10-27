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

![创建令牌]

## 设置令牌

![设置令牌]

## 修改`_config.yml`

- `xing2000.coding.me`是仓库名
- `xing2000`是用户名

```yml
deploy:
  type: git
  name: 星
  email: i@star2000.work
  repo: https://xing2000:TENCENT_TOKEN@git.dev.tencent.com/xing2000/xing2000.coding.me
```

## 创建`.github/workflows/deploy.yml`

```yml
on:
  - push

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: 安装nodejs
        uses: actions/setup-node@master
        with:
          node-version: "*"

      - name: 下载源码
        run: git clone --depth=1 https://github.com/${{ github.repository }} .

      - name: 下载主题
        run: git clone --depth=1 https://github.com/theme-next/hexo-theme-next themes/next

      - name: 安装依赖
        run: npm i --production

      - name: 设置令牌
        run: sed -i "s/TENCENT_TOKEN/${{ secrets.TENCENT_TOKEN }}/" _config.yml

      - name: 部署
        run: ./node_modules/.bin/hexo d
```

[github操作]: https://help.github.com/cn/articles/workflow-syntax-for-github-actions
[hexo]: https://hexo.io
[创建令牌]: 创建令牌.png
[设置令牌]: 设置令牌.png
