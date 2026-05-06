---
title: "openclaw config"
sidebarTitle: "config"
---

# `openclaw config`

`config` 用来读取、修改、校验 `openclaw.json`。它适合脚本和高级用户；新手如果不确定路径，优先用 `openclaw configure` 交互向导。

常用：

```bash
openclaw config file
openclaw config get agents.defaults.model.primary
openclaw config set plugins.entries.tokenjuice.enabled true
openclaw config validate
openclaw config schema
```

## 什么时候用

- 想看当前配置文件在哪里。
- 想在脚本里设置某个明确的配置路径。
- 想校验配置是否能被 Gateway 读取。
- 想把配置 schema 交给编辑器或 CI。

## 新手提醒

`config set` 会直接写配置。路径写错可能不会达到你想要的效果，所以改完一定跑：

```bash
openclaw config validate
openclaw doctor
```

继续阅读：[配置参考](/tutorials/gateway/configuration-reference)。
