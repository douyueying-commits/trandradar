# GitHub 小白发布指南（不写命令版）

你只需要会“点按钮”，按这份做就行。

---

## 先解决你现在的报错（No GitHub repositories found）

这个报错的意思是：

- 你本地文件夹已经是 Git 仓库 ✅
- 但它还不是“GitHub 仓库”（还没绑定 GitHub 远程地址）❗

按下面 6 步就能修好：

1. 浏览器打开 https://github.com/new
2. Repository name 填：`Trendradar`（或你喜欢的名字）
3. 不要勾选 README（保持空仓库）
4. 点 **Create repository**
5. 回到 VS Code，按 `Ctrl+Shift+P`，输入并选择：`Git: Add Remote`
6. Remote name 填 `origin`，URL 填：`https://github.com/你的用户名/你的仓库名.git`

完成后，这个错误就会消失。

---

## 0. 准备账号（只做一次）

1. 打开 https://github.com
2. 注册账号并登录

---

## 1. 在 VS Code 里把项目发到 GitHub

> 不用终端，不用 git 命令。

1. 打开本项目文件夹（就是你现在的 `Trendradar`）
2. 点击左侧 **源代码管理**（分支图标）
3. 如果看到 **初始化仓库**，点击它
4. 在上方输入提交说明（比如：`first publish`）
5. 点击 **提交**
6. 点击 **发布到 GitHub**（Publish to GitHub）
7. 选择 `Public`（想给别人用，建议公开）
8. 等待上传完成

完成后，VS Code 会给你一个 GitHub 仓库链接。

---

## 2. 开启必须设置（网页点几下）

### A) 开启 Actions 写权限

进入仓库网页后：

`Settings -> Actions -> General -> Workflow permissions`

选择：
- ✅ **Read and write permissions**

---

### B) 开启静态页面（给别人访问）

`Settings -> Pages`

- Source: **Deploy from a branch**
- Branch: 选 `main`（或 `master`）
- Folder: **/(root)**
- 点 Save

稍等 1~2 分钟，会出现访问地址：

`https://你的用户名.github.io/你的仓库名/app.html`

这个就是发给别人用的链接。

---

## 3. 首次手动跑一次

`Actions -> Get Hot News -> Run workflow`

- 第一次跑完后，页面内容就会更新
- 访问 `.../app.html` 检查是否看到报告

---

## 4. 长期使用（非常重要）

每 7 天做一次：

`Actions -> Check In -> Run workflow`

否则自动任务会暂停。

---

## 5. 可选：配置消息推送

如果你想把热点推送到手机/群里，再去设置 Secrets（比如飞书/企微/Telegram）。

入口：

`Settings -> Secrets and variables -> Actions -> New repository secret`

---

## 6. 常见问题

### 看不到“发布到 GitHub”
- 先确认你已登录 VS Code 的 GitHub 账号（右下角/头像菜单）

### 页面打不开
- 检查 Pages 是否启用到分支根目录 `/(root)`
- 等 1~2 分钟再刷新

### 内容不更新
- 去 Actions 看 `Get Hot News` 是否成功
- 确认日志里有 `Commit updated static page`
