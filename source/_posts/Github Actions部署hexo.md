---
title: Github Actions部署hexo
date: 2019-08-29 09:06:07
tags:
  - hexo
  - 自动部署
---
使用[Github Actions]自动部署[hexo]博客
<!--more-->
## 创建令牌

![创建令牌](创建令牌.png)

## 设置令牌

![设置令牌](设置令牌.png)

## 修改`_config.yml`

```yml
deploy:
  type: git
  name: 星
  email: i@star2000.work
  repo: https://star2000:CODING_TOKEN@e.coding.net/CODING_REPO
```

## 创建`.github/workflows/deploy.yml`

```yml
on:
  push

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/setup-node@master
        with:
          node-version: "*"
      - uses: actions/checkout@master
      - uses: actions/checkout@master
        with:
          repository: theme-next/hexo-theme-next
          path: themes/next
      - run: |
          sed -i "s|CODING_TOKEN|${{ secrets.CODING_TOKEN }}|" _config.yml
          sed -i "s|CODING_REPO|${{ secrets.CODING_REPO }}|" _config.yml
          npm i --production
          npm run deploy
```

[Github Actions]: https://help.github.com/cn/actions/reference/workflow-syntax-for-github-actions
[hexo]: https://hexo.io
