---
title: Shadowsocks User Guide
split_at: 2
version: 1.0.0
---

# Shadowsocks User Guide

## Connection Information

Login to the server via SSH to view the following information:

| Item           | Description                              |
| -------------- | ---------------------------------------- |
| Server Address | Your Server Public IP                    |
| Server Port    | Configured Port Number                   |
| Password       | Configured Password                      |
| Encryption     | E.g. aes-256-gcm                         |
| Management Dir | `/opt/cloud/shadowsocks`                 |
| Credentials    | `/opt/cloud/shadowsocks/credentials.txt` |

## Common Operations

```bash
cd /opt/cloud/shadowsocks

./start.sh            # Start service
./stop.sh             # Stop service
./restart.sh          # Restart service
./status.sh           # Check status
./logs.sh             # View logs
./change_password.sh  # Change password
```

## Client Configuration

### Windows

**Shadowsocks-Windows** (Recommended):

1. Download: [GitHub Releases](https://github.com/shadowsocks/shadowsocks-windows/releases)
2. Run `Shadowsocks.exe` → Right-click tray icon → Servers → Edit Servers
3. Fill in connection info → OK → Right-click Enable System Proxy

**Proxy Mode**: PAC Mode (Proxy blocked sites only) or Global Mode (All traffic)

### macOS

**ShadowsocksX-NG** (Recommended):

1. Download: [GitHub Releases](https://github.com/shadowsocks/ShadowsocksX-NG/releases)
2. Unzip and drag to Applications → Click paper plane icon in menu bar → Servers → Server Settings
3. Click "+" to add server → Fill in connection info → Turn Shadowsocks On

### Linux

**Install shadowsocks-libev**:

```bash
# Ubuntu/Debian
sudo apt update && sudo apt install shadowsocks-libev

# CentOS/RHEL
sudo yum install epel-release && sudo yum install shadowsocks-libev

# Arch Linux
sudo pacman -S shadowsocks-libev
```

**Create Configuration File**:

```bash
sudo mkdir -p /etc/shadowsocks
sudo nano /etc/shadowsocks/config.json
```

```json
{
    "server": "<Server_IP>",
    "server_port": <Port>,
    "local_address": "127.0.0.1",
    "local_port": 1080,
    "password": "<Password>",
    "timeout": 300,
    "method": "<Encryption_Method>"
}
```

**Start Service**:

```bash
sudo systemctl start shadowsocks-libev-local@config
sudo systemctl enable shadowsocks-libev-local@config
```

**Configure System Proxy**: SOCKS Host `127.0.0.1`, Port `1080`

## Troubleshooting

| Issue                     | Solution                                                  |
| ------------------------- | --------------------------------------------------------- |
| Auth Failure              | Check if password and encryption match server config      |
| Connection Timeout        | Verify Server IP, check if firewall blocks port           |
| Connected but no internet | Check local proxy settings, try switching PAC/Global mode |

**Open Firewall Port**:

```bash
sudo ufw allow <Port>/tcp
```

## Learn More

- [Shadowsocks Official Documentation](https://shadowsocks.org/)
- [Shadowsocks-libev GitHub](https://github.com/shadowsocks/shadowsocks-libev)
