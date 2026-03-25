# 🔀 版本控制 Git

> Git 是 DevOps 的核心工具，必须熟练掌握

---

## 🎯 学习目标

- 理解 Git 的工作原理
- 熟练使用 Git 基本命令
- 掌握分支管理和合并策略
- 理解 Git 工作流（GitHub Flow / GitLab Flow）

---

## 📚 学习资源

### 互动教程（强烈推荐）

#### 1. **Learn Git Branching**
- **链接：** https://learngitbranching.js.org/
- **特点：** 可视化学 Git，超级直观
- **语言：** 支持中文
- **时长：** 2-3 天闯关
- **推荐关卡：**
  - Main: Introduction Sequence
  - Remote: Push & Pull

#### 2. **Git Immersion**
- **链接：** https://gitimmersion.com/
- **特点：** 52 个小练习，循序渐进
- **时长：** 1-2 天

### 视频教程

#### 3. **Git and GitHub for Beginners - FreeCodeCamp**
- **链接：** https://www.youtube.com/watch?v=RGOj5yH7evk
- **时长：** 1 小时
- **特点：** 快速上手，覆盖核心操作

#### 4. **Git & GitHub Crash Course - Traversy Media**
- **链接：** https://www.youtube.com/watch?v=SWYqp7iY_Tc
- **时长：** 30 分钟
- **特点：** 实战导向，讲得清楚

### 文档资源

#### 5. **Pro Git（官方免费电子书）**
- **链接：** https://git-scm.com/book/zh/v2
- **作者：** Scott Chacon & Ben Straub
- **特点：** 最权威的 Git 教程，中文版免费
- **推荐章节：**
  - 第 1 章：起步
  - 第 2 章：Git 基础
  - 第 3 章：Git 分支

#### 6. **GitHub Skills**
- **链接：** https://skills.github.com/
- **特点：** GitHub 官方互动教程
- **推荐课程：**
  - Introduction to GitHub
  - Resolve Merge Conflicts

---

## 🧠 核心概念

### Git 的三个区域

```
工作区 (Working Directory)
    ↓  git add
暂存区 (Staging Area / Index)
    ↓  git commit
版本库 (Repository / .git directory)
```

### 基本工作流

```bash
# 1. 克隆仓库
git clone https://github.com/user/repo.git

# 2. 修改文件
# ... 编辑代码 ...

# 3. 查看状态
git status

# 4. 添加到暂存区
git add file.txt
git add .  # 添加所有修改

# 5. 提交
git commit -m "Add new feature"

# 6. 推送到远程
git push origin main
```

---

## 🛠️ 常用命令

### 基础操作

```bash
# 初始化仓库
git init

# 克隆仓库
git clone <url>

# 查看状态
git status

# 添加文件到暂存区
git add <file>
git add .

# 提交
git commit -m "Commit message"

# 查看提交历史
git log
git log --oneline --graph

# 查看差异
git diff
git diff --staged
```

### 分支管理

```bash
# 创建分支
git branch feature-x

# 切换分支
git checkout feature-x
# 或者 (新版本)
git switch feature-x

# 创建并切换
git checkout -b feature-x
# 或者
git switch -c feature-x

# 查看所有分支
git branch
git branch -a  # 包括远程分支

# 合并分支
git checkout main
git merge feature-x

# 删除分支
git branch -d feature-x
```

### 远程操作

```bash
# 查看远程仓库
git remote -v

# 添加远程仓库
git remote add origin <url>

# 拉取更新
git pull origin main

# 推送
git push origin main

# 拉取远程分支
git fetch origin
```

### 撤销操作

```bash
# 撤销工作区的修改
git checkout -- <file>
# 或者 (新版本)
git restore <file>

# 撤销暂存区的文件
git reset HEAD <file>
# 或者
git restore --staged <file>

# 撤销最后一次提交（保留修改）
git reset --soft HEAD~1

# 撤销最后一次提交（丢弃修改）
git reset --hard HEAD~1

# 修改最后一次提交
git commit --amend
```

### 高级操作

```bash
# Rebase（重新应用提交）
git rebase main

# Cherry-pick（挑选提交）
git cherry-pick <commit-hash>

# Stash（暂存工作进度）
git stash
git stash list
git stash apply
git stash pop

# 查看某个文件的历史
git log -p <file>

# 查看某一行的修改历史
git blame <file>
```

---

## 🌳 Git 工作流

### GitHub Flow（推荐入门）

```
main (生产分支)
  ↓
feature-branch (功能分支)
  ↓
Pull Request (代码审查)
  ↓
合并回 main
```

**流程：**
1. 从 `main` 创建功能分支
2. 在功能分支上开发
3. 提交 Pull Request
4. 代码审查
5. 合并回 `main`
6. 删除功能分支

### GitLab Flow（进阶）

```
main → pre-production → production
```

---

## 🎯 实战练习

### 练习 1：基本操作
1. 创建一个新仓库
2. 添加几个文件并提交
3. 修改文件，查看 `git diff`
4. 提交修改
5. 查看 `git log`

### 练习 2：分支操作
1. 创建一个新分支 `feature-login`
2. 在分支上添加功能
3. 切回 `main` 分支
4. 合并 `feature-login`
5. 删除 `feature-login` 分支

### 练习 3：解决冲突
1. 创建两个分支，修改同一个文件的同一行
2. 尝试合并
3. 解决冲突
4. 完成合并

### 练习 4：GitHub 操作
1. 在 GitHub 上创建仓库
2. 本地克隆
3. 推送代码
4. 创建 Pull Request
5. 合并 PR

---

## 📖 Git 速查表

- **GitHub Git Cheat Sheet：** https://education.github.com/git-cheat-sheet-education.pdf
- **Atlassian Git Cheat Sheet：** https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet

---

## 💡 最佳实践

1. **提交信息清晰**
   ```bash
   # ✅ Good
   git commit -m "Fix: Resolve login timeout issue"
   
   # ❌ Bad
   git commit -m "fix bug"
   ```

2. **经常提交，小步快跑**
   - 一个提交只做一件事
   - 不要把多个功能混在一个提交里

3. **拉取前先提交**
   ```bash
   git add .
   git commit -m "WIP: Save current work"
   git pull origin main
   ```

4. **永远不要** `git push -f` **到主分支**

---

## ✅ 阶段检查

完成后，你应该能：
- [ ] 能 clone、add、commit、push、pull
- [ ] 理解分支的概念并能熟练操作
- [ ] 能解决简单的合并冲突
- [ ] 知道 rebase 和 cherry-pick 的区别
- [ ] 能在 GitHub 上提 PR 并参与代码审查

---

## 下一步

→ [实战项目](./project.md)

---

**上一级：** [返回第一阶段目录](./README.md)
