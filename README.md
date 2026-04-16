# ppt

本地幻灯与 GitHub Pages 部署说明。

## 外网访问（GitHub Pages · `/docs`）

本仓库将可发布的静态页放在 **`docs/`** 目录：`docs/index.html` 由 `share_框架增强版.html` 同步而来，作为站点首页。

### 一次性配置

1. 在 GitHub 上新建一个空仓库（例如 `ppt` 或任意名称），**不要**勾选自动添加 README（若已添加也可）。
2. 在本目录执行（将 `YOUR_USER` / `YOUR_REPO` 换成你的账号与仓库名）：

```bash
git init
git add docs .gitignore README.md
git commit -m "Add GitHub Pages site under docs"
git branch -M main
git remote add origin https://github.com/YOUR_USER/YOUR_REPO.git
git push -u origin main
```

3. 打开 GitHub 仓库：**Settings → Pages**  
   - **Build and deployment → Source**：选 **Deploy from a branch**  
   - **Branch**：选 `main`，文件夹选 **`/docs`**  
   - Save  

4. 等待约 1～2 分钟，访问：

`https://YOUR_USER.github.io/YOUR_REPO/`

即为 `docs/index.html` 的线上地址。

### 更新幻灯内容

修改根目录 `share_框架增强版.html` 后，复制到 `docs/index.html` 再提交推送：

```bash
copy share_框架增强版.html docs\index.html
git add docs\index.html
git commit -m "Update deck"
git push
```

（macOS / Linux 使用 `cp share_框架增强版.html docs/index.html`。）

### 说明

- 已添加 **`docs/.nojekyll`**，避免 GitHub 用 Jekyll 处理静态文件时出现意外。
- 幻灯内使用的 Google Fonts 等外链需能访问外网；若内网环境受限，可后续改为本地字体。
