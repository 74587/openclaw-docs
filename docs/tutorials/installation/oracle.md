---
title: "Oracle Cloud 部署"
sidebarTitle: "Oracle Cloud"
description: "OpenClaw 安装部署：在 Oracle Cloud Always Free ARM 实例上运行 OpenClaw。"
---

# Oracle Cloud 部署

Oracle Cloud Always Free ARM 实例可以免费跑一台长期在线的 Linux 机器。
它适合愿意折腾云账号和网络规则的用户。

---

## 推荐思路

1. 创建 Ubuntu 24.04 ARM 实例。
2. 用 SSH 登录。
3. 安装基础编译工具。
4. 安装 Tailscale。
5. 安装 OpenClaw。
6. 用 `openclaw onboard --install-daemon` 配置 Gateway。
7. 用 Tailscale 或 SSH 隧道访问控制 UI。

---

## 安装命令

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential curl git
curl -fsSL https://openclaw.ai/install.sh | bash
openclaw onboard --install-daemon
```

---

## 为什么推荐 Tailscale

Oracle 免费实例容易被误配置成公网暴露。
Tailscale 可以让你的电脑、手机、服务器像在同一个私人局域网里。

```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up --ssh --hostname=openclaw
```

然后尽量关闭不必要的公网入站规则。

---

## 注意事项

- 免费实例容量可能抢不到，失败可以换可用区或稍后重试。
- ARM 架构下某些二进制工具要选 arm64 版本。
- 不要开放 `18789` 到公网。
- 定时任务要确认服务器时区。

