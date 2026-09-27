# meph1st0 的博客

使用 Hugo、PaperMod 和 Emacs `ox-hugo`，发布地址为 <https://blog.meph1st0.top>。

## 写文章

在 `content-org/` 新建 `.org` 文件，例如 `my-post.org`：

```org
#+title: 文章标题
#+author: meph1st0
#+description: 一行摘要
#+date: 2026-09-28T10:00:00+08:00
#+hugo_base_dir: ..
#+hugo_section: posts
#+hugo_front_matter_format: yaml
#+hugo_tags: 技术
#+export_file_name: my-post

这里写正文。可以使用 Org 的标题、列表、链接和代码块。
```

在 Emacs 中打开文章，运行 `C-c C-e H H`（`org-hugo-export-wim-to-md`）。导出的 Markdown 会写入 `content/posts/`。`content-org/` 是写作源文件；修改文章后要重新导出。当前 Emacs 配置已安装 `ox-hugo`。

也可以在文章的 Org buffer 中按 `C-c o b`（`my/blog-publish-current-buffer`）：它会保存文章、导出 Markdown、运行 Hugo 构建、只提交当前文章的 `.org` 和 `.md` 文件并推送 `main`。命令只接受本仓库 `content-org/` 下的文件，且要求本地 `main` 与远端同步；若推送失败，本地提交会保留，可在问题解决后运行 `git push origin main`。

在仓库中提交 `.org` 源文件和对应的 `.md` 导出文件，然后推送到 `main`。GitHub Actions 会使用 Hugo 构建并发布：

```sh
git add content-org/my-post.org content/posts/my-post.md
git commit -m "Add my post"
git push origin main
```

现有首篇文章的 `#+hugo_url` 固定了旧地址 `/2026/09/27/welcome/`。以后如需指定文章地址，也可在 Org 文件中加入 `#+hugo_url: /想要的地址/`。

## 本地预览

首次克隆后运行 `git submodule update --init --recursive` 获取 PaperMod，然后运行 `hugo server -D`，访问 <http://localhost:1313>。`hugo` 可用于正式构建。

## 发布设置

仓库的 GitHub Pages **Build and deployment → Source** 需要设为 **GitHub Actions**。工作流位于 `.github/workflows/deploy.yml`，`static/CNAME` 保留自定义域名 `blog.meph1st0.top`；RSS 地址是 `/feed.xml`。
