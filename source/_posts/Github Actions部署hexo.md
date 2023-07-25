---
title: Github Actions部署hexo
date: 2019-08-29 09:06:07
tags:
  - hexo
  - 自动部署
---

使用[Github Actions]自动部署[hexo]博客

<!--more-->

## 创建`.github/workflows/deploy.yml`

```yml .github/workflows/deploy.yml
name: deploy

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0
          submodules: true
      - name: 恢复上次修改时间
        run: git ls-files -z | while read -d '' path; do touch -d "$(git log -1 --format="@%ct" "$path")" "$path"; done
      - uses: actions/setup-node@v3
        with:
          node-version: lts/*
      - run: yarn install
      - run: yarn run build
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

[github actions]: https://docs.github.com/zh/actions
[hexo]: https://hexo.io
