---
title: "openclaw update"
sidebarTitle: "update"
---

# `openclaw update`

`update` 用来更新 OpenClaw。源码安装、全局包安装、稳定版、beta、dev 通道的细节不完全一样，所以升级前先看清自己是哪种安装方式。

```bash
openclaw update
openclaw update status
openclaw update --dry-run
openclaw update --channel beta
openclaw update --no-restart
openclaw doctor
openclaw gateway restart
```

## 新手最稳路线

先做预演：

```bash
openclaw update --dry-run
```

确认没问题再更新：

```bash
openclaw update
```

更新完做体检：

```bash
openclaw doctor
openclaw status
```

如果 Gateway 没有自动重启，手动重启：

```bash
openclaw gateway restart
```

## 常用选项

- `--dry-run`：只看看会发生什么，不真正改。
- `--no-restart`：更新后不自动重启 Gateway。
- `--channel stable|beta|dev`：切换更新通道。
- `--yes`：自动确认，适合无人值守脚本。
- `--json`：给脚本读取的 JSON 输出。

## 升级后先查什么

1. `openclaw status` 看版本和 Gateway 是否在线。
2. `openclaw doctor` 看配置是否需要迁移。
3. `openclaw plugins doctor` 看插件是否还兼容。
4. `openclaw channels status --probe` 看聊天通道是否真的能连。

继续阅读：[更新 OpenClaw](/tutorials/installation/updating)。
