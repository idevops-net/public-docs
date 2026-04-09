---
title: Shadowsocks 使用指南
split_at: 2
version: 1.0.0
---

# Shadowsocks 使用指南

## 连接信息

通过 SSH 登录服务器查看以下信息：

| 项目         | 说明                                     |
| ------------ | ---------------------------------------- |
| 服务器地址   | 您的服务器公网 IP                        |
| 服务器端口   | 配置的端口号                             |
| 密码         | 配置的密码                               |
| 加密方法     | 如 aes-256-gcm                           |
| 管理脚本目录 | `/opt/cloud/shadowsocks`                 |
| 凭证文件     | `/opt/cloud/shadowsocks/credentials.txt` |

## 常用操作

```bash
cd /opt/cloud/shadowsocks

./start.sh            # 启动服务
./stop.sh             # 停止服务
./restart.sh          # 重启服务
./status.sh           # 查看状态
./logs.sh             # 查看日志
./change_password.sh  # 修改密码
```

## 客户端配置

### Windows

**Shadowsocks-Windows**（推荐）：

1. 下载：[GitHub Releases](https://github.com/shadowsocks/shadowsocks-windows/releases)
2. 运行 `Shadowsocks.exe` → 右键托盘图标 → 服务器 → 编辑服务器
3. 填写连接信息 → 确定 → 右键启用系统代理

**代理模式**：PAC 模式（仅代理被墙网站）或全局模式（所有流量）

### macOS

**ShadowsocksX-NG**（推荐）：

1. 下载：[GitHub Releases](https://github.com/shadowsocks/ShadowsocksX-NG/releases)
2. 解压拖入应用程序 → 菜单栏点击纸飞机 → 服务器 → 服务器设置
3. 点击「+」添加服务器 → 填写连接信息 → 打开 Shadowsocks

### Linux

**安装 shadowsocks-libev**：

```bash
# Ubuntu/Debian
sudo apt update && sudo apt install shadowsocks-libev

# CentOS/RHEL
sudo yum install epel-release && sudo yum install shadowsocks-libev

# Arch Linux
sudo pacman -S shadowsocks-libev
```

**创建配置文件**：

```bash
sudo mkdir -p /etc/shadowsocks
sudo nano /etc/shadowsocks/config.json
```

```json
{
    "server": "<服务器IP>",
    "server_port": <端口号>,
    "local_address": "127.0.0.1",
    "local_port": 1080,
    "password": "<密码>",
    "timeout": 300,
    "method": "<加密方法>"
}
```

**启动服务**：

```bash
sudo systemctl start shadowsocks-libev-local@config
sudo systemctl enable shadowsocks-libev-local@config
```

**配置系统代理**：SOCKS 主机 `127.0.0.1`，端口 `1080`

## 常见问题

| 问题             | 解决方案                                   |
| ---------------- | ------------------------------------------ |
| 认证失败         | 检查密码和加密方法是否与服务器一致         |
| 连接超时         | 确认服务器 IP 正确，检查防火墙是否开放端口 |
| 连接上但无法访问 | 检查本地代理设置，尝试切换 PAC/全局模式    |

**开放防火墙端口**：

```bash
sudo ufw allow <端口号>/tcp
```

## 深入学习

- [Shadowsocks 官方文档](https://shadowsocks.org/)
- [Shadowsocks-libev GitHub](https://github.com/shadowsocks/shadowsocks-libev)
