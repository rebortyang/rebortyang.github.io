---
title: Github Actions 初体验
date: 2019-10-03 13:27:28
tags:
    - 部落格
categories:
    - 学习
    - github
---

尝试运用GitHub actions部署GitHub pages。

<!-- more -->

## 开始

### 生成部署的key

```bash
ssh-keygen -t rsa -b 4096 -C "$(git config user.email)" -f gh-pages -N ""
# You will get 2 files:
#   gh-pages.pub (public key)
#   gh-pages     (private key)
```

### 设置仓库

在你的GitHub pages仓库的设置里面添加*Deploy Keys*和*Secrets*

### 新建你的workflow

在你的代码目录中新建 `.github/workflows/gh-pages.yml`文件，并将它push到master。  
（pass：gh-pages.yml名称自定）

### 资料
[阮一峰部落格](http://www.ruanyifeng.com/blog/2019/09/getting-started-with-github-actions.html)  
[GitHub Actions for GitHub Pages](https://github.com/peaceiris/actions-gh-pages) 
