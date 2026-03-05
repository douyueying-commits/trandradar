# TrendRadar 无服务器长期部署（静态页展示）

## 1) 把工作流文件放到你的仓库

- `.github/workflows/crawler.yml`
- `.github/workflows/clean-crawler.yml`

## 2) 在 GitHub 仓库里开启 Actions 权限

仓库 `Settings -> Actions -> General`：

- Workflow permissions 选择 **Read and write permissions**
- 勾选 **Allow GitHub Actions to create and approve pull requests**（可选）

## 3) 配置最少 Secrets（先跑起来）

至少配置一个推送渠道，否则虽然会生成页面但你收不到通知：

- 例如飞书：`FEISHU_WEBHOOK_URL`

可选（长期强烈建议，完整能力）：

- `STORAGE_BACKEND=remote`
- `S3_BUCKET_NAME`
- `S3_ACCESS_KEY_ID`
- `S3_SECRET_ACCESS_KEY`
- `S3_ENDPOINT_URL`
- `S3_REGION`（可选）

## 4) 开启 GitHub Pages

仓库 `Settings -> Pages`：

- Source 选 **Deploy from a branch**
- Branch 选你的默认分支（`main` 或 `master`）
- Folder 选 **/(root)**

> 页面地址一般是：
> `https://<你的用户名>.github.io/<仓库名>/`

## 5) 首次验证

- 打开 `Actions -> Get Hot News -> Run workflow`
- 等 1~3 分钟
- 检查最新一次运行日志中是否出现 `Commit updated static page`
- 打开 Pages 地址确认页面已更新

## 6) 长期维护

- 每 7 天手动运行一次：`Actions -> Check In -> Run workflow`
- 如需改频率，修改 `.github/workflows/crawler.yml` 中 cron

## 常见问题

### 页面不更新

优先检查：

1. `crawler.yml` 的 `permissions.contents` 是否为 `write`
2. 仓库 Actions 权限是否为 Read and write
3. 运行日志里是否出现 `No index.html changes, skip commit`
4. GitHub Pages 是否部署的是默认分支根目录

### workflow 过期停跑

- 手动执行一次 `Check In`
- 如果 `Get Hot News` 被禁用，先在 Actions 页重新启用再执行
