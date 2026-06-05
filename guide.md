# 🚀 傻瓜式发布指南：将张文庆学长访谈发布到 GitBook

本指南手把手带你完成从零到上线的完整流程。**不需要任何编程或 Git 经验**，跟着步骤操作即可。

---

## 📋 前置准备

### 1. GitHub 账号

如果没有，去 [https://github.com/signup](https://github.com/signup) 注册一个。用户名建议用你的英文名，邮箱建议用 `theodorelee@sjtu.edu.cn`。

✅ 登录 [https://github.com](https://github.com)，能看到个人主页即可。

### 2. 确认 Git 已安装

打开 PowerShell（右键开始菜单 → Windows PowerShell），输入：

```bash
git --version
```

如果显示类似 `git version 2.xx.x`，说明已安装。

如果提示"不是内部或外部命令"：去 [https://git-scm.com/download/win](https://git-scm.com/download/win) 下载安装，安装时一路点"下一步"即可。

### 3. 文件已就绪

确认桌面上有 `sjtu-alumni-interviews` 文件夹，里面包含：

```
sjtu-alumni-interviews/
├── SUMMARY.md
├── index.md        ← 访谈正文
└── guide.md        ← 你正在读的这个文件
```

---

## 📦 Part A：推送到 GitHub

### A1. 创建 GitHub 仓库

1. 打开 [https://github.com/new](https://github.com/new)
2. 填写：

   | 字段 | 内容 |
   |:---|:---|
   | Repository name | `sjtu-alumni-interviews` |
   | Description | `上海交通大学物理与天文学院校友访谈录` |
   | Public / Private | **Public**（GitBook 免费版要求公开） |

3. ⚠️ **不要勾选** "Add a README file"、"Add .gitignore"、"Choose a license"
4. 点绿色的 **"Create repository"**

✅ 看到空仓库的快速设置页面即为成功。

### A2. 复制仓库地址

在刚创建的仓库页面，复制文本框里的地址，类似：

```
https://github.com/你的用户名/sjtu-alumni-interviews.git
```

### A3. 配置 Git（仅第一次需要）

打开 PowerShell，依次输入（替换名字和邮箱）：

```bash
git config --global user.name "你的名字"
git config --global user.email "theodorelee@sjtu.edu.cn"
git config --global core.quotepath false
```

### A4. 推送文件

在 PowerShell 中：

```bash
cd "C:\Users\Li Zhenghong\Desktop\Temp\sjtu-alumni-interviews"
```

然后逐条执行：

```bash
git init
git add .
git commit -m "Initial commit: 张文庆学长访谈报告"
git branch -M main
git remote add origin https://github.com/你的用户名/sjtu-alumni-interviews.git
git push -u origin main
```

> ⚠️ 推送时如果弹出 GitHub 登录窗口，点浏览器授权即可。
> 如果命令行让你输入用户名密码，见底部 Q1 故障排查。

✅ 刷新 GitHub 仓库页面，能看到 `index.md` 和 `SUMMARY.md` 即成功。

---

## 🔗 Part B：连接 GitBook 与 GitHub

### B1. 打开 GitBook 设置

1. 打开你的 GitBook 空间：[https://app.gitbook.com/o/Vpjfq1TsNCLkOQYmLfLv/s/CtS5kmt6RMS6ALNvLoSB/](https://app.gitbook.com/o/Vpjfq1TsNCLkOQYmLfLv/s/CtS5kmt6RMS6ALNvLoSB/)
2. 点右上角 **⚙️ 齿轮图标** → 左侧菜单选 **Git Sync**

### B2. 配置同步

1. 选择 **GitHub** 作为同步来源
2. 按提示授权 GitBook 访问 GitHub
3. ⚠️ 关键步骤：GitHub 会让你选 "Install GitBook" 到哪些仓库：
   - 选 **"Only select repositories"**
   - 下拉菜单中选 `sjtu-alumni-interviews`
   - 点 Install
4. 回到 GitBook 页面，选择：
   - Repository：`你的用户名/sjtu-alumni-interviews`
   - Branch：`main`
   - 同步方向：**GitHub → GitBook**
5. 点 **"Enable Sync"**

✅ GitBook 左侧边栏出现页面内容即成功。

### B3. 检查效果

确认标题、Q&A 格式、分割线都正确显示。

---

## 🌐 Part C：发布上线

1. 在 GitBook 右上角点 **"Publish"**
2. 可见性建议先选 **Unlisted**（有链接才能访问），确认无误后再改为 Public
3. 发布后会得到一个链接，格式如：`https://xxx.gitbook.io/sjtu-alumni-interviews`

✅ 用浏览器的无痕模式打开链接，确认可正常访问。

---

## 🔄 Part D：后续修改

- **在线编辑**：GitBook 里点 "Edit" 直接改 → 点 "Merge" 保存，自动同步回 GitHub
- **本地编辑**：修改 `index.md` → 重新执行以下命令：
  ```bash
  cd "C:\Users\Li Zhenghong\Desktop\Temp\sjtu-alumni-interviews"
  git add .
  git commit -m "Update content"
  git push
  ```

---

## 🛠️ 常见问题

### Q1：`git push` 报 "Authentication failed"

GitHub 2021 年起不支持密码登录，需用 Token：

1. 打开 [https://github.com/settings/tokens](https://github.com/settings/tokens)
2. 点 "Generate new token (classic)"
3. Note 填 `git-push`，过期选 "No expiration"
4. 勾选 **repo** 整个分类
5. 点 "Generate token"，**立即复制**（以 `ghp_` 开头）
6. 命令行提示输密码时，粘贴这个 token

### Q2：GitBook 同步后页面为空

检查 Git Sync 设置里同步方向是 **GitHub → GitBook**（不是 GitBook → GitHub）。

### Q3：中文乱码

执行：
```bash
git config --global core.quotepath false
git config --global i18n.commitencoding utf-8
```

---

> 发布顺利！🎉
