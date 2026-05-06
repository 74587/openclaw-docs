---
title: "Control UI"
sidebarTitle: "Control UI"
---

# Control UI：浏览器里的 OpenClaw 控制台

Control UI 是你管理 OpenClaw 的浏览器界面。它可以查看 Gateway、通道、节点、模型、任务和会话状态。

打开方式：

```bash
openclaw dashboard
```

默认地址通常是：

```text
http://127.0.0.1:18789/
```

如果你远程访问，请走 Tailscale、VPN、SSH 隧道或可信反向代理，并配置认证。

继续阅读：[Gateway 认证](/tutorials/gateway/authentication)、[Web 控制 UI](/tutorials/web/)

## 新手提醒

Control UI 很方便，但它也是管理入口。远程访问时一定要保护好：

- 使用 token 或密码。
- 不裸露到公网。
- 不把带 token 的 URL 发给别人。
- 服务器优先用 SSH tunnel 或 Tailscale。
