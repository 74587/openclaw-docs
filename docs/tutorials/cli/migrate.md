---
title: "openclaw migrate"
sidebarTitle: "migrate"
---

# `openclaw migrate`

`migrate` 用来把 Claude、Hermes 或旧版状态迁到 OpenClaw。迁移属于高风险操作，因为它可能碰到凭据、会话、技能、配置路径。

先预览：

```bash
openclaw migrate claude --dry-run
openclaw migrate hermes --dry-run
```

## 新手路线

1. 先备份当前 OpenClaw：

```bash
openclaw backup create --verify
```

2. 再预览迁移：

```bash
openclaw migrate claude --dry-run
```

3. 看清楚会复制什么，再执行真正迁移。

## 迁移后检查

```bash
openclaw doctor
openclaw status
openclaw plugins list
```

继续阅读：[从 Claude 迁移](/tutorials/installation/migrating-claude)。
