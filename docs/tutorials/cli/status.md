---
title: "openclaw status"
sidebarTitle: "status"
---

# `openclaw status`

`status` 用来看 OpenClaw 当前是否健康。它是排障时最适合先跑的命令之一。

```bash
openclaw status
openclaw status --deep
openclaw status --all
openclaw status --json
```

## 它会告诉你什么

- Gateway 是否在线。
- 当前版本和更新信息。
- 模型、provider、运行时的大概状态。
- 任务、会话、节点、服务是否正常。
- 某些 SecretRef 或凭据是否可读。

## `status`、`--all`、`--deep` 怎么选

- `openclaw status`：最快，适合日常看一眼。
- `openclaw status --all`：更完整，适合升级后检查。
- `openclaw status --deep`：会做更多真实探测，适合排障。
- `openclaw status --json`：给脚本和 CI 用。

## 排障三连

```bash
openclaw status --all
openclaw doctor
openclaw logs --follow
```

如果 status 说 Gateway 不在线，再看：

```bash
openclaw gateway status
openclaw gateway restart
```

继续阅读：[Gateway 总览](/tutorials/gateway/)。
