# 🌐 网络基础

> 理解网络是怎么工作的，才能排查问题和优化性能

---

## 🎯 学习目标

- 理解 TCP/IP 协议栈
- 掌握 DNS 工作原理
- 理解 HTTP/HTTPS
- 会用基本的网络诊断工具
- 能配置简单的防火墙

---

## 📚 学习资源

### 视频教程

#### 1. **Networking for Beginners - Practical Networking**
- **链接：** https://www.practicalnetworking.net/series/networking-fundamentals/
- **特点：** 图文并茂，概念清晰
- **推荐章节：**
  - OSI Model
  - TCP/IP
  - Subnetting
  - Routing
- **时长：** 1 周

#### 2. **FreeCodeCamp - Computer Networking Course**
- **链接：** https://www.youtube.com/watch?v=qiQR5rTSshw
- **时长：** 9 小时完整课程
- **特点：** 从零到深入，适合系统学习

### 文档资源

#### 3. **MDN - HTTP 文档**
- **链接：** https://developer.mozilla.org/en-US/docs/Web/HTTP
- **特点：** 权威的 HTTP 协议文档
- **推荐阅读：**
  - HTTP Messages
  - HTTP Methods
  - HTTP Status Codes
  - HTTP Headers

#### 4. **Julia Evans - Networking Zines**
- **链接：** https://wizardzines.com/zines/networking/
- **特点：** 漫画风格，轻松易懂（付费，但有免费样章）

---

## 🧠 核心概念

### 1. TCP/IP 四层模型

```
应用层 (Application)    →  HTTP, DNS, SSH, FTP
传输层 (Transport)      →  TCP, UDP
网络层 (Internet)       →  IP, ICMP
链路层 (Link)           →  Ethernet, Wi-Fi
```

**重点理解：**
- TCP vs UDP 的区别
- IP 地址和子网掩码
- 端口号的作用

### 2. DNS（域名系统）

```
你输入: example.com
↓
浏览器查 DNS: example.com 的 IP 是什么？
↓
DNS 返回: 93.184.216.34
↓
浏览器连接: 93.184.216.34:80
```

**常用 DNS 工具：**
```bash
# 查询域名对应的 IP
nslookup example.com
dig example.com

# 查看 DNS 缓存
cat /etc/resolv.conf
```

### 3. HTTP/HTTPS

**HTTP 请求结构：**
```http
GET /api/users HTTP/1.1
Host: example.com
User-Agent: curl/7.68.0
Accept: application/json
```

**HTTP 响应结构：**
```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 123

{"users": [...]}
```

**常用状态码：**
- `200 OK` — 成功
- `301/302` — 重定向
- `400 Bad Request` — 客户端错误
- `401 Unauthorized` — 未授权
- `404 Not Found` — 资源不存在
- `500 Internal Server Error` — 服务器错误
- `502 Bad Gateway` — 网关错误
- `503 Service Unavailable` — 服务不可用

---

## 🛠️ 实用工具

### 网络诊断

```bash
# 测试连通性
ping google.com

# 追踪路由
traceroute google.com

# 查看端口是否开放
telnet example.com 80
nc -zv example.com 80

# 抓包分析
tcpdump -i eth0 port 80

# 查看网络连接
netstat -tuln
ss -tuln

# 测试 HTTP
curl -I https://example.com
curl -v https://example.com
```

### 防火墙管理

#### iptables（传统方式）
```bash
# 查看规则
sudo iptables -L

# 允许 80 端口
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

# 禁止某个 IP
sudo iptables -A INPUT -s 192.168.1.100 -j DROP
```

#### firewalld（现代方式，推荐）
```bash
# 查看状态
sudo firewall-cmd --state

# 开放 80 端口
sudo firewall-cmd --permanent --add-port=80/tcp
sudo firewall-cmd --reload

# 查看已开放端口
sudo firewall-cmd --list-ports
```

#### ufw（Ubuntu 简化版）
```bash
# 启用防火墙
sudo ufw enable

# 允许 SSH
sudo ufw allow 22/tcp

# 允许 HTTP/HTTPS
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# 查看状态
sudo ufw status
```

---

## 🎯 实战练习

### 练习 1：DNS 查询
用 `dig` 查询 `google.com` 的 A 记录、MX 记录、TXT 记录

### 练习 2：HTTP 测试
用 `curl` 测试一个 API：
- 发送 GET 请求
- 发送 POST 请求（带 JSON body）
- 查看响应头

### 练习 3：端口扫描
用 `nmap` 扫描本地服务器，找出开放的端口

### 练习 4：配置防火墙
在测试服务器上：
1. 只允许 SSH (22)、HTTP (80)、HTTPS (443)
2. 禁止其他所有入站流量

---

## 📖 推荐阅读

- **《图解 TCP/IP》** —— 适合入门，图文并茂
- **《HTTP 权威指南》** —— 深入理解 HTTP 协议
- **Cloudflare Learning Center** —— https://www.cloudflare.com/learning/

---

## ✅ 阶段检查

完成后，你应该能：
- [ ] 解释 TCP/IP 四层模型
- [ ] 理解 DNS 工作原理并能诊断 DNS 问题
- [ ] 能用 `curl` 测试 API
- [ ] 能配置简单的防火墙规则
- [ ] 能用 `netstat`/`ss` 查看网络连接

---

## 下一步

→ [版本控制 Git](./03-git.md)

---

**上一级：** [返回第一阶段目录](./README.md)
