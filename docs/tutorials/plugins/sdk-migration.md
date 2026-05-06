---
title: "SDK Migration"
sidebarTitle: "SDK 迁移"
---

# SDK Migration

SDK 迁移是插件跟随 OpenClaw 版本升级时要做的适配。

推荐做法：

1. 看 release notes。
2. 更新 manifest。
3. 更新 SDK import。
4. 跑插件测试。
5. 在测试 Gateway 里验证。

不要直接在生产 Gateway 上试破坏性迁移。

## 新手迁移顺序

1. 备份。
2. 在测试 Gateway 启用新版本插件。
3. 跑 `openclaw plugins doctor`。
4. 做一条真实请求。
5. 看日志和安全审计。

确认稳定后再动生产环境。
