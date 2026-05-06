---
title: "openclaw plugins"
sidebarTitle: "plugins"
---

# `openclaw plugins`

`plugins` 用来管理 Gateway 插件。插件可以给 OpenClaw 增加通道、模型 provider、工具、搜索、语音、诊断等能力。

把它想成手机里的“应用管理”：先安装，再启用，出问题就体检。

```bash
openclaw plugins list
openclaw plugins list --enabled
openclaw plugins enable <name>
openclaw plugins disable <name>
openclaw plugins install <path-or-spec>
openclaw plugins inspect <id>
openclaw plugins doctor
```

## 什么时候用

- 新接入一个官方或社区插件。
- 升级后发现某个通道、模型或工具不见了。
- 想确认某个插件到底有没有启用。
- 插件报错，需要看 manifest、runtime 或诊断结果。

## 新手最稳路线

1. 先看现状：

```bash
openclaw plugins list --verbose
```

2. 安装插件：

```bash
openclaw plugins install @openclaw/example
```

3. 启用插件：

```bash
openclaw plugins enable example
```

4. 重启或检查 Gateway：

```bash
openclaw gateway restart
openclaw plugins doctor
```

## 看不懂输出怎么办

先记三件事：

- `enabled` 表示已经启用。
- `disabled` 表示装了但没开。
- `Format: openclaw` 表示原生 OpenClaw 插件；`Format: bundle` 表示兼容包。

如果安装很慢或失败，再加生命周期追踪：

```bash
OPENCLAW_PLUGIN_LIFECYCLE_TRACE=1 openclaw plugins install <path-or-spec>
```

继续阅读：[插件专题](/tutorials/plugins/)。
