---
title: Github Actions部署hexo
date: 2019-08-29 09:06:07
tags:
  - hexo
  - 自动部署
permalink:
---

使用[Github Actions]自动部署[hexo]博客

<!--more-->

## 创建令牌

![创建令牌](创建令牌.png)

## 设置令牌

`CODING_TOKEN`的格式是`令牌用户名:令牌`

![设置令牌](设置令牌.png)

## 修改`_config.yml`

```yml _config.yml
deploy:
  type: git
  name: star2000
  email: i@star2000.work
  repo: https://CODING_TOKEN@e.coding.net/xing2000/blog/deploy
```

## 创建`.github/workflows/deploy.yml`

```yml .github/workflows/deploy.yml
on: push

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
        with:
          fetch-depth: 0
          submodules: true
      - name: 恢复上次修改时间
        run: git ls-files -z | while read -d '' path; do touch -d "$(git log -1 --format="@%ct" "$path")" "$path"; done
      - uses: actions/setup-node@master
        with:
          node-version: "*"
      - name: 部署
        run: |
          sed -i "s|CODING_TOKEN|${{ secrets.CODING_TOKEN }}|" _config.yml
          npm i --production
          npm run deploy
```

[github actions]: https://help.github.com/cn/actions/reference/workflow-syntax-for-github-actions
[hexo]: https://hexo.io
