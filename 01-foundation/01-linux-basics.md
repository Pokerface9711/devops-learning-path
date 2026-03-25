# 🐧 Linux 基础

> 学会在 Linux 上干活，这是 DevOps 的基本功

---

## 🎯 学习目标

- 熟练使用 Linux 命令行
- 理解文件系统和权限
- 会写基础 Shell 脚本
- 能远程管理服务器

---

## 📚 学习资源

### 免费资源（推荐从这里开始）

#### 1. **Linux Journey**
- **链接：** https://linuxjourney.com/
- **特点：** 互动式教程，从零开始，循序渐进
- **推荐章节：**
  - Grasshopper（初学者）
  - Journeyman（进阶）
- **时长：** 1-2 周

#### 2. **The Linux Command Line（免费电子书）**
- **链接：** https://linuxcommand.org/tlcl.php
- **作者：** William Shotts
- **特点：** 经典教材，PDF 免费下载
- **推荐章节：**
  - Part 1: Learning the Shell
  - Part 2: Configuration and Environment
  - Part 4: Writing Shell Scripts

#### 3. **OverTheWire: Bandit（游戏化学习）**
- **链接：** https://overthewire.org/wargames/bandit/
- **特点：** 通过闯关学 Linux，超级有趣
- **难度：** 初级到中级
- **时长：** 边玩边学，1-2 周

### 视频教程

#### 4. **FreeCodeCamp - Linux for Ethical Hackers**
- **链接：** https://www.youtube.com/watch?v=U1w4T03B30I
- **时长：** 2.5 小时
- **特点：** 实战导向，覆盖核心命令

#### 5. **Corey Schafer - Linux/Mac Terminal Tutorial**
- **链接：** https://www.youtube.com/playlist?list=PL-osiE80TeTvGhHkpvfmKWOiIPF8UVXjm
- **时长：** 系列短视频
- **特点：** 清晰易懂，适合快速上手

### 实战平台

#### 6. **Katacoda / KillerCoda**
- **链接：** https://killercoda.com/
- **特点：** 浏览器里练 Linux，无需本地环境
- **推荐场景：**
  - Linux Basics
  - Shell Scripting

---

## 🛠️ 必学命令清单

### 文件管理
```bash
ls          # 列出文件
cd          # 切换目录
pwd         # 显示当前路径
mkdir       # 创建目录
rm          # 删除文件/目录
cp          # 复制
mv          # 移动/重命名
touch       # 创建空文件
cat         # 查看文件内容
less/more   # 分页查看
head/tail   # 查看文件头/尾
```

### 权限管理
```bash
chmod       # 修改权限
chown       # 修改所有者
ls -l       # 查看详细权限
```

### 进程管理
```bash
ps          # 查看进程
top/htop    # 实时监控
kill        # 杀进程
bg/fg       # 后台/前台
jobs        # 查看后台任务
```

### 网络工具
```bash
ping        # 测试连通性
curl        # HTTP 请求
wget        # 下载文件
ssh         # 远程登录
scp         # 远程复制文件
rsync       # 同步文件
netstat/ss  # 查看网络连接
```

### 文本处理
```bash
grep        # 搜索文本
sed         # 流编辑器
awk         # 文本分析
cut         # 切割文本
sort        # 排序
uniq        # 去重
wc          # 统计行数/字数
```

### 系统管理
```bash
sudo        # 提权执行
apt/yum     # 包管理
systemctl   # 服务管理
df          # 磁盘使用
du          # 目录大小
free        # 内存使用
uname       # 系统信息
```

---

## 📝 Shell 脚本入门

### 基础脚本结构
```bash
#!/bin/bash
# 这是注释

# 变量
NAME="World"
echo "Hello, $NAME"

# 条件
if [ "$NAME" = "World" ]; then
    echo "Name is World"
fi

# 循环
for i in 1 2 3; do
    echo "Number: $i"
done

# 函数
greet() {
    echo "Hello, $1"
}
greet "DevOps"
```

### 学习资源
- **Bash 脚本教程：** https://www.shellscript.sh/
- **Bash 速查表：** https://devhints.io/bash

---

## 🎯 实战练习

### 练习 1：文件批量重命名
写一个脚本，把目录下所有 `.txt` 文件改成 `.md`

### 练习 2：自动备份脚本
写一个脚本，自动备份指定目录到 `/backup/`，并打上时间戳

### 练习 3：日志分析
用 `grep`、`awk`、`sort` 分析 nginx 访问日志，找出访问最多的 IP

---

## ✅ 阶段检查

完成后，你应该能：
- [ ] 不用 GUI，纯命令行管理服务器
- [ ] 能写 50 行以上的 bash 脚本解决实际问题
- [ ] 能用 `ssh` 连接远程服务器并配置服务
- [ ] 理解 Linux 文件权限和用户管理

---

## 下一步

→ [网络基础](./02-networking.md)

---

**上一级：** [返回第一阶段目录](./README.md)
