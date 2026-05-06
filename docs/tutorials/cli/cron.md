---
title: "openclaw cron"
sidebarTitle: "cron"
---

# `openclaw cron`

管理定时任务。

适合“每天早上发简报”“每周跑报告”这类固定时间任务。

```bash
openclaw cron list
openclaw cron show <jobId>
openclaw cron add --help
openclaw cron run <jobId>
```

## 什么时候用

- 固定时间自动执行任务。
- 想查看定时任务是否还在。
- 某个定时任务失败，需要看最近运行记录。

## 新手提醒

定时任务依赖 Gateway 在线、时间设置正确、模型和通道可用。
如果没触发，先看：

```bash
openclaw cron list
openclaw tasks list
openclaw logs --follow
```

继续阅读：[Cron 定时任务](/tutorials/automation/cron-jobs)。

## 常见误会

Cron 只负责“到点触发”。触发后能不能成功，还取决于模型、工具、通道和权限。
所以 cron 失败时，也要同时看 `tasks` 和日志。
