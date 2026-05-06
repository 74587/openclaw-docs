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
- `--json`：给脚本读取的 JSON 输出。新版本会把插件同步问题放在 `postUpdate.plugins` 里。

## 看懂更新结果

如果你运行：

```bash
openclaw update --json
```

看到顶层 `status: "ok"`，通常说明 OpenClaw 主程序已经更新成功。

但还要继续看 `postUpdate.plugins`：

- `status: "ok"`：插件也同步好了。
- `status: "warning"`：主程序更新成功，但某个托管插件损坏、无法加载，或者 npm 插件产物校验不一致。
- `warnings`：告诉你哪个插件需要修。
- `integrityDrifts`：告诉你 npm 插件安装出来的文件和期望校验值不一样。

遇到 `warning` 不要慌，先按顺序做：

```bash
openclaw doctor --fix
openclaw plugins inspect <插件ID> --runtime --json
openclaw plugins doctor
```

如果你不知道 `<插件ID>` 是什么，先运行：

```bash
openclaw plugins list
```

::: tip 给奶奶看的解释
更新像给家里换总电闸。`status: "ok"` 说明总电闸换好了；`postUpdate.plugins.status: "warning"` 说明某个插座接触不好。先修插座，不要重复拆总电闸。
:::

## dev 通道的预检查变化

如果你使用 `dev` 通道，更新前会在临时目录里先跑 TypeScript 构建。
如果最新提交构建失败，它会往前找最多 10 个提交，选择最新一个能构建成功的版本。

默认不会跑 lint，因为很多用户的小机器比 CI 慢。确实需要 lint 时，再这样开：

```bash
OPENCLAW_UPDATE_PREFLIGHT_LINT=1 openclaw update --channel dev
```

普通用户用 `stable` 通道时，不需要管这一段。

## 升级后先查什么

1. `openclaw status` 看版本和 Gateway 是否在线。
2. `openclaw doctor` 看配置是否需要迁移。
3. `openclaw plugins doctor` 看插件是否还兼容。
4. `openclaw channels status --probe` 看聊天通道是否真的能连。

继续阅读：[更新 OpenClaw](/tutorials/installation/updating)。
