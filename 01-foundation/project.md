# 🚀 第一阶段实战项目

> 把学到的东西用起来！

---

## 🎯 项目目标

搭建一个个人服务器，部署一个简单的 web 服务，并用 Git 管理代码。

完成后，你会有：
- 一个可以通过域名访问的网站
- Git 仓库管理的代码
- 基本的服务器运维经验

---

## 📋 项目要求

### 必做
- ✅ 在云服务器上部署一个静态网站（Nginx）
- ✅ 配置 SSH 密钥登录（禁用密码登录）
- ✅ 配置防火墙（只开放必要端口）
- ✅ 用 Git 管理网站代码
- ✅ 写一个部署脚本（bash）

### 加分项
- 🌟 配置 HTTPS（Let's Encrypt）
- 🌟 配置域名解析
- 🌟 设置自动备份脚本
- 🌟 配置日志轮转

---

## 🛠️ 实施步骤

### Step 1：准备服务器

#### 选择云服务商
- **阿里云：** https://www.aliyun.com/product/ecs
- **腾讯云：** https://cloud.tencent.com/product/cvm
- **AWS：** https://aws.amazon.com/ec2/
- **DigitalOcean：** https://www.digitalocean.com/

**推荐配置：**
- CPU: 1 核
- 内存: 1-2 GB
- 系统: Ubuntu 22.04 LTS

#### 登录服务器
```bash
ssh root@your-server-ip
```

---

### Step 2：配置 SSH 密钥登录

#### 生成 SSH 密钥（本地）
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

#### 上传公钥到服务器
```bash
ssh-copy-id root@your-server-ip
```

#### 禁用密码登录（服务器上）
```bash
sudo vi /etc/ssh/sshd_config

# 修改以下配置
PasswordAuthentication no
PermitRootLogin prohibit-password

# 重启 SSH 服务
sudo systemctl restart sshd
```

---

### Step 3：安装 Nginx

```bash
# 更新包列表
sudo apt update

# 安装 Nginx
sudo apt install nginx -y

# 启动 Nginx
sudo systemctl start nginx
sudo systemctl enable nginx

# 查看状态
sudo systemctl status nginx
```

**测试：** 浏览器访问 `http://your-server-ip`，应该能看到 Nginx 欢迎页面

---

### Step 4：部署网站

#### 创建网站目录
```bash
sudo mkdir -p /var/www/mysite
sudo chown -R $USER:$USER /var/www/mysite
```

#### 创建 HTML 文件
```bash
cat > /var/www/mysite/index.html <<EOF
<!DOCTYPE html>
<html>
<head>
    <title>My First DevOps Project</title>
</head>
<body>
    <h1>Hello, DevOps!</h1>
    <p>This is my first server deployment.</p>
</body>
</html>
EOF
```

#### 配置 Nginx
```bash
sudo vi /etc/nginx/sites-available/mysite

# 添加以下内容
server {
    listen 80;
    server_name your-domain.com;  # 或者 your-server-ip

    root /var/www/mysite;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}

# 启用站点
sudo ln -s /etc/nginx/sites-available/mysite /etc/nginx/sites-enabled/

# 测试配置
sudo nginx -t

# 重启 Nginx
sudo systemctl reload nginx
```

---

### Step 5：配置防火墙

```bash
# 安装 ufw
sudo apt install ufw -y

# 允许 SSH
sudo ufw allow 22/tcp

# 允许 HTTP/HTTPS
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# 启用防火墙
sudo ufw enable

# 查看状态
sudo ufw status
```

---

### Step 6：Git 管理代码

#### 初始化 Git 仓库
```bash
cd /var/www/mysite
git init
git add .
git commit -m "Initial commit"
```

#### 推送到 GitHub
```bash
# 在 GitHub 创建一个新仓库

# 添加远程仓库
git remote add origin https://github.com/your-username/mysite.git

# 推送代码
git branch -M main
git push -u origin main
```

---

### Step 7：写部署脚本

创建 `deploy.sh`：

```bash
#!/bin/bash

# 部署脚本
# 功能：从 Git 拉取最新代码并重启 Nginx

set -e  # 遇到错误立即退出

echo "🚀 Starting deployment..."

# 进入项目目录
cd /var/www/mysite

# 备份当前版本
echo "📦 Backing up current version..."
tar -czf /tmp/mysite-backup-$(date +%Y%m%d-%H%M%S).tar.gz *

# 拉取最新代码
echo "📥 Pulling latest code from Git..."
git pull origin main

# 重启 Nginx
echo "🔄 Reloading Nginx..."
sudo systemctl reload nginx

echo "✅ Deployment completed successfully!"
```

赋予执行权限：
```bash
chmod +x deploy.sh
```

---

## 🌟 加分项实现

### 配置 HTTPS（Let's Encrypt）

```bash
# 安装 Certbot
sudo apt install certbot python3-certbot-nginx -y

# 获取证书
sudo certbot --nginx -d your-domain.com

# 自动续期
sudo certbot renew --dry-run
```

### 配置自动备份

创建 `backup.sh`：

```bash
#!/bin/bash

BACKUP_DIR="/backup/mysite"
DATE=$(date +%Y%m%d-%H%M%S)

mkdir -p $BACKUP_DIR
tar -czf $BACKUP_DIR/mysite-$DATE.tar.gz /var/www/mysite

# 只保留最近 7 天的备份
find $BACKUP_DIR -type f -mtime +7 -delete

echo "Backup completed: $BACKUP_DIR/mysite-$DATE.tar.gz"
```

添加 cron 任务（每天凌晨 2 点备份）：
```bash
crontab -e

# 添加
0 2 * * * /path/to/backup.sh
```

---

## ✅ 验收标准

完成后，你应该能：
- [ ] 通过域名或 IP 访问你的网站
- [ ] 用 SSH 密钥（非密码）登录服务器
- [ ] 修改网站内容并用 Git 提交
- [ ] 运行部署脚本自动更新网站
- [ ] 防火墙只开放必要端口
- [ ] （加分项）网站支持 HTTPS

---

## 📸 提交作业

完成后，在 `progress.md` 里记录：
1. 服务器 IP 或域名
2. GitHub 仓库链接
3. 遇到的问题和解决方法
4. 截图（可选）

---

## 🎓 学到了什么？

通过这个项目，你已经掌握了：
- ✅ 服务器基本配置
- ✅ Nginx 部署静态网站
- ✅ SSH 安全配置
- ✅ 防火墙管理
- ✅ Git 版本控制
- ✅ Shell 脚本自动化

**恭喜你！第一阶段完成！** 🎉

---

## 下一步

→ [第二阶段：CI/CD 管道](../02-cicd/README.md)

---

**上一级：** [返回第一阶段目录](./README.md)
