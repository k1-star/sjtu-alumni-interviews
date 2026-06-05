# 🚀 傻瓜式发布指南：将张文庆学长访谈发布到 GitBook

本指南将手把手带你完成从零到上线的完整流程。**不需要任何编程或 Git 经验**，只要跟着步骤操作即可。

每个步骤末尾都有 ✅ 验证项，帮你确认操作是否成功。

---

## 📋 前置准备

在开始之前，请确认以下三项已就绪：

### 1. GitHub 账号

- 如果没有，去 [https://github.com/signup](https://github.com/signup) 注册一个
- 用户名建议：`theodorelee` 或你的英文名
- 注册邮箱建议用 `theodorelee@sjtu.edu.cn`

✅ **验证**：登录 [https://github.com](https://github.com)，能看到你的个人主页

### 2. 确认 Git 已安装（Windows）

打开"命令提示符"或 PowerShell，输入：

```bash
git --version
```

如果显示类似 `git version 2.xx.x`，说明已安装。
如果提示"不是内部或外部命令"：

1. 去 [https://git-scm.com/download/win](https://git-scm.com/download/win) 下载安装
2. 安装时一路点"下一步"即可（所有选项保持默认）

✅ **验证**：重新打开命令行，输入 `git --version`，能看到版本号

### 3. 文件已就绪

确认你的桌面（或指定目录）有一个文件夹叫 `sjtu-alumni-interviews`，里面包含以下文件：

```
sjtu-alumni-interviews/
├── SUMMARY.md
├── index.md
├── chapter-01.md
├── chapter-02.md
├── chapter-03.md
├── postscript.md
└── guide.md          ← 你正在读的这个文件
```

✅ **验证**：打开文件夹，能看到上述 7 个文件

---

## 📦 Part A：推送到 GitHub

### A1. 在 GitHub 上创建新仓库

1. 浏览器打开 [https://github.com/new](https://github.com/new)
2. 填写以下信息：

   | 字段 | 填写内容 |
   |:---|:---|
   | Repository name | `sjtu-alumni-interviews` |
   | Description | `上海交通大学物理与天文学院校友访谈录` |
   | Public / Private | 选择 **Public**（公开，GitBook 免费版要求） |

3. ⚠️ **不要勾选** "Add a README file"
4. ⚠️ **不要勾选** "Add .gitignore"
5. ⚠️ **不要勾选** "Choose a license"
6. 点击绿色的 **"Create repository"** 按钮

✅ **验证**：页面跳转到新仓库，显示一个空仓库的快速设置指南

### A2. 复制仓库地址

在刚创建的仓库页面，你会看到一个文本框，里面是类似这样的地址：

```
https://github.com/theodorelee/sjtu-alumni-interviews.git
```

点击右侧的 📋 复制按钮，把地址复制下来。

✅ **验证**：地址已复制到剪贴板

### A3. 配置 Git（仅第一次需要）

打开命令行（PowerShell 或 Git Bash），依次输入以下两条命令（把名字和邮箱替换成你自己的）：

```bash
git config --global user.name "你的名字"
git config --global user.email "theodorelee@sjtu.edu.cn"
```

再输入这条，确保中文文件名能正常显示：

```bash
git config --global core.quotepath false
```

✅ **验证**：无报错提示

### A4. 推送文件到 GitHub

在命令行中，先进入你放文件的那个文件夹。假设文件夹在桌面上：

```bash
cd "C:\Users\Li Zhenghong\Desktop\Temp\sjtu-alumni-interviews"
```

然后依次执行以下每一条命令（一行一行来，等每一步完成再输入下一步）：

```bash
# 第 1 步：初始化 Git 仓库
git init

# 第 2 步：添加所有文件
git add .

# 第 3 步：提交（创建第一个版本）
git commit -m "Initial commit: 张文庆学长访谈报告"

# 第 4 步：把默认分支改名为 main
git branch -M main

# 第 5 步：关联远程仓库（把下面地址替换成你在 A2 复制的地址）
git remote add origin https://github.com/theodorelee/sjtu-alumni-interviews.git

# 第 6 步：推送到 GitHub（会弹出一个窗口让你登录 GitHub，点授权即可）
git push -u origin main
```

> ⚠️ 第 6 步如果弹出 GitHub 登录窗口，点击"Sign in with your browser"，在浏览器中授权即可。如果命令行里提示输入用户名和密码，用户名填你的 GitHub 用户名，密码需要在 GitHub 上生成一个 Personal Access Token（见下方故障排查）。

✅ **验证**：刷新 GitHub 仓库页面，能看到所有 `.md` 文件都在里面了！

---

## 🔗 Part B：连接 GitBook 与 GitHub

### B1. 打开 GitBook 空间设置

1. 浏览器打开你的 GitBook 空间：
   [https://app.gitbook.com/o/Vpjfq1TsNCLkOQYmLfLv/s/CtS5kmt6RMS6ALNvLoSB/](https://app.gitbook.com/o/Vpjfq1TsNCLkOQYmLfLv/s/CtS5kmt6RMS6ALNvLoSB/)
2. 点击右上角的 **齿轮图标 ⚙️**（Settings）
3. 在左侧菜单中找到并点击 **Git Sync**

### B2. 配置 Git Sync

1. 在 Git Sync 页面，点击 **GitHub** 作为同步来源
2. 点击 **"Install GitBook on GitHub"** 或 **"Link GitHub account"**
3. 按提示授权 GitBook 访问你的 GitHub 账号
4. ⚠️ 关键步骤：GitHub 会让你选择 "Install GitBook" 到哪些仓库：
   - 选择 **"Only select repositories"**
   - 在下拉菜单中选择 `sjtu-alumni-interviews`
   - 点击 Install
5. 回到 GitBook 页面，选择：
   - **GitHub repository**：`theodorelee/sjtu-alumni-interviews`
   - **Branch**：`main`
6. 点击 **"Enable Sync"** 或 **"Start Sync"**

✅ **验证**：GitBook 左侧边栏出现你的所有页面（index、第一章、第二章、第三章、后记）

### B3. 检查渲染效果

逐一打开 GitBook 侧边栏的每个页面，确认：

- [ ] 各级标题（H1、H2、H3）正确显示
- [ ] Q&A 格式清晰，问题和回答有区分
- [ ] 绿色提示框（{% hint style="success" %}）正确渲染为带颜色的卡片
- [ ] 蓝色提示框（{% hint style="info" %}）正确渲染
- [ ] 黄色提示框（{% hint style="warning" %}，在第二章）正确渲染
- [ ] 侧边栏导航可以正常点击跳转

✅ **验证**：所有页面格式正确，没有显示原始 `{% hint %}` 代码

---

## 🌐 Part C：发布上线

### C1. 发布空间

1. 在 GitBook 空间右上角，找到 **"Publish"** 按钮（或空间名称旁边的下拉箭头）
2. 点击后会看到发布设置：
   - **Visibility**（可见性）：选择你需要的选项
     - Public（公开）：任何人都能访问
     - Unlisted（不公开列出）：只有知道链接的人能访问
     - Members only（仅成员）：需要邀请才能访问
   - 建议先选 **Unlisted**，确认内容无误后再改为 Public
3. 点击 **"Publish"**

### C2. 获取分享链接

发布成功后，你会获得一个链接，格式类似：

```
https://your-org.gitbook.io/sjtu-alumni-interviews
```

✅ **验证**：用浏览器的无痕/隐私模式打开这个链接，确认可以正常访问

---

## 🔄 Part D：后续维护

### 如何修改内容？

方法一（推荐，最简单）：直接在 GitBook 网页端编辑
1. 打开 GitBook 空间，点击右上角 **"Edit"** 按钮
2. 进入编辑模式，像编辑 Word 一样修改内容
3. 修改完成后，点击 **"Merge"** 或 **"Submit change request"**
4. 改动会自动同步回 GitHub

方法二：修改 GitHub 上的 Markdown 文件
1. 打开 GitHub 仓库中的 `.md` 文件
2. 点击右上角 ✏️ 编辑按钮
3. 修改后点击 "Commit changes"
4. GitBook 会自动检测到更新并重新同步

### 如何添加新的访谈？

1. 在本地文件夹中新建一个 `.md` 文件（如 `chapter-04.md`）
2. 在 `SUMMARY.md` 中加上新文件的链接
3. 重复 Part A 中的步骤 A4 的最后两步（commit + push）：
   ```bash
   cd "C:\Users\Li Zhenghong\Desktop\Temp\sjtu-alumni-interviews"
   git add .
   git commit -m "Add new interview: XXX"
   git push
   ```

---

## 🛠️ 常见问题排查

### Q1：`git push` 时报错 "Authentication failed"

**原因**：GitHub 从 2021 年起不再支持密码登录，需要使用 Personal Access Token。

**解决**：
1. 打开 [https://github.com/settings/tokens](https://github.com/settings/tokens)
2. 点击 "Generate new token (classic)"
3. Note 填 `git-push`，Expiration 选 "No expiration"
4. 勾选 `repo` 这一整个分类
5. 点击底部的 "Generate token"
6. **立即复制**生成的 token（以 `ghp_` 开头）——离开页面后就看不到了！
7. 回到命令行，当提示输入密码时，**粘贴这个 token**（不是你的 GitHub 密码）

### Q2：中文文件在 GitHub 上显示乱码

**原因**：Windows 的 git 默认编码问题。

**解决**：执行以下命令后重新操作：
```bash
git config --global core.quotepath false
git config --global i18n.commitencoding utf-8
git config --global i18n.logoutputencoding utf-8
```

### Q3：GitBook 同步后页面是空的

**可能原因**：
1. `SUMMARY.md` 中的文件名和实际文件名不匹配（包括大小写）
2. Git Sync 方向选错了，选成了 "GitBook -> GitHub"

**解决**：
- 回到 GitBook 设置 → Git Sync，确认同步方向是 **GitHub → GitBook**
- 检查 SUMMARY.md 中的文件名与仓库中的文件名完全一致

### Q4：{% hint %} 代码显示为原始文本，没有渲染成彩色框

**可能原因**：
1. `{% hint %}` 语法格式有误（多了一个空格、少了一个 `%` 等）
2. 没有用 `{% endhint %}` 闭合

**解决**：
- 检查格式，必须是：
  ```
  {% hint style="info" %}
  内容
  {% endhint %}
  ```
- `style` 可以是 `info`（蓝）、`success`（绿）、`warning`（黄）、`danger`（红）

### Q5：想用中文文件名可以吗？

可以！把文件名改成比如 `第一章-专深与广博.md`，然后在 `SUMMARY.md` 里对应修改即可。只是 URL 中会出现百分号编码的中文，不影响使用。

---

## 📞 需要帮助？

如果在操作过程中遇到任何问题：
- 把命令行中的**错误信息**截图
- 发邮件到 `theodorelee@sjtu.edu.cn`，或在 GitBook 空间的评论区留言

---

> **祝你发布顺利！🎉**
