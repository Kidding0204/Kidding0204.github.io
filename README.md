# meph1st0 的博客

使用 GitHub Pages 内置的 Jekyll 构建，发布地址为 <https://blog.meph1st0.top>。

## 写文章

在 `_posts/` 新建 `YYYY-MM-DD-title.md`，例如：

```markdown
---
layout: post
title: "文章标题"
description: "一行摘要"
date: 2026-09-27 21:00:00 +0800
tags: [技术]
---

文章正文，支持 Markdown。
```

推送到 `main` 后，GitHub Pages 会自动构建。站点信息在 `_config.yml`，页面样式在 `assets/style.css`。

## 本地预览

安装 Ruby 和 Bundler 后运行 `bundle install`、`bundle exec jekyll serve`，然后访问 <http://localhost:4000>。

## 域名

Pages 的自定义域名设置为 `blog.meph1st0.top`。DNS 应将 `blog` 的 CNAME 指向 GitHub 账号的 `<username>.github.io`，并在 Pages 设置中启用 HTTPS。
