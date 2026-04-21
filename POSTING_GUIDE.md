# 博客发文操作指南（Hexo / GitHub Pages）

你这个仓库目前保存的是**已生成的静态站点文件**（`index.html`、`archives/`、`tags/` 等），不是完整的 Hexo 源码目录。

## 先判断你现在是哪种工作流

### 方案 A（推荐）——你有 Hexo 源码仓库
如果你有另一个仓库（或另一个分支）保存了 `source/`、`themes/`、`_config.yml`，那就按标准 Hexo 流程写作。

### 方案 B（当前仓库现状）——只有生成后的静态文件
这个仓库直接放的是生成结果，不适合直接写 Markdown 发文。
要继续长期写博客，建议你恢复/新建 Hexo 源码目录，再生成后发布到这个 `AlbertHello.github.io` 仓库。

---

## 标准 Hexo 发文流程（你后续照这个做）

### 1) 新建文章
```bash
hexo new post "我的新文章标题"
```
会生成：
```text
source/_posts/我的新文章标题.md
```

### 2) Markdown 文件放哪里？
放在：
```text
source/_posts/
```

### 3) Markdown 里的图片放哪里？（两种常用方案）

#### 方案 1：统一图片目录（简单）
- 图片放：`source/images/`（或 `source/uploads/`）
- md 中写：
```md
![示例图](/images/xxx.png)
```

#### 方案 2：文章同名资源目录（推荐长期维护）
先在 Hexo 配置里打开：
```yml
post_asset_folder: true
```
然后每篇文章会有同名资源目录，例如：
```text
source/_posts/我的新文章标题.md
source/_posts/我的新文章标题/cover.png
```
md 中引用（配合 asset_img 标签）：
```md
{% asset_img cover.png 封面图 %}
```

> 这套方式最适合你后续文章多了以后管理图片。

### 4) 本地预览
```bash
hexo clean && hexo g && hexo s
```
浏览器打开 `http://localhost:4000` 查看效果。

### 5) 发布到 GitHub Pages
```bash
hexo clean && hexo g
```
把 `public/` 里的生成内容发布到 `AlbertHello.github.io` 仓库根目录。

---

## 你当前仓库的实用建议

1. 这个仓库继续只放静态产物（部署稳定）。
2. 另建一个私有/公开仓库存 Hexo 源码（写作舒适）。
3. 每次写完文章后，本地生成，再把 `public/*` 同步到这个仓库并提交。

