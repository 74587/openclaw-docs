---
title: "Raspberry Pi 部署"
sidebarTitle: "Raspberry Pi"
description: "OpenClaw 安装部署：在树莓派上运行 24 小时在线的 Gateway。"
---

# Raspberry Pi 部署

树莓派适合做家里的小型 OpenClaw Gateway。
模型通常仍然走云端 API，所以树莓派主要负责收消息、调度、保存状态。

---

## 推荐硬件

- Raspberry Pi 4 或 5
- 2GB 内存起步，4GB 更稳
- 64 位 Raspberry Pi OS
- 稳定电源
- 有线网络或稳定 Wi-Fi
- SD 卡或 USB SSD

不要使用 32 位系统。

---

## 安装步骤

SSH 登录树莓派后：

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y git curl build-essential
curl -fsSL https://deb.nodesource.com/setup_24.x | sudo -E bash -
sudo apt install -y nodejs
curl -fsSL https://openclaw.ai/install.sh | bash
openclaw onboard --install-daemon
```

低内存设备建议加 swap：

```bash
sudo fallocate -l 2G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

---

## 访问控制 UI

从你的电脑建立隧道：

```bash
ssh -N -L 18789:127.0.0.1:18789 user@gateway-host
```

然后打开：

```text
http://127.0.0.1:18789/
```

长期远程访问可以看 [Tailscale](/tutorials/gateway/tailscale)。

