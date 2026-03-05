# 分享给别人使用：最短路径

你现在有两个可访问页面：

- `index.html`：原始报告页（每次任务自动更新）
- `app.html`：应用入口页（适合对外分享，带安装和分享按钮）

---

## 1) 提交并推送到你的 GitHub 仓库

把以下文件提交到仓库：

- `.github/workflows/crawler.yml`
- `.github/workflows/clean-crawler.yml`
- `app.html`
- `app-manifest.webmanifest`
- `app-sw.js`
- `icons/icon-192.png`
- `icons/icon-512.png`

---

## 2) 启用 GitHub Pages

仓库设置：`Settings -> Pages`

- Source: **Deploy from a branch**
- Branch: 你的默认分支（`main` 或 `master`）
- Folder: **/(root)**

发布后应用入口链接一般是：

- `https://<你的用户名>.github.io/<仓库名>/app.html`

> 建议对外分享这个 `app.html` 链接。

---

## 3) 首次运行检查

- `Actions -> Get Hot News -> Run workflow`
- 运行成功后，确认日志出现 `Commit updated static page`
- 打开 `app.html` 链接，能看到最新报告即成功

---

## 4) 长期维护（必须做）

- 每 7 天运行一次：`Actions -> Check In -> Run workflow`

否则定时任务会因到期自动停掉。

---

## 5) 想让更多人稳定访问（可选）

- 绑定自定义域名（比如 `radar.yourdomain.com`）
- 在仓库 `Settings -> Pages` 里配置 `Custom domain`
- 开启 HTTPS

这样你分享的链接会更像正式应用。
