---
title: "SDK Subpaths"
sidebarTitle: "SDK Subpaths"
---

# SDK Subpaths

SDK subpaths 让插件按需引用不同能力模块，而不是一次引入所有东西。

好处：

- 依赖更清楚。
- 打包更轻。
- 能力边界更明确。

如果你只写 provider 插件，就引用 provider 相关 SDK。不要把 channel、tool、runtime 都混进来。

## 新手提醒

subpath 像工具箱里的分格。你只拿需要的那一格，代码更清楚，未来 SDK 调整时也更容易迁移。

插件作者写 import 时，优先使用官方文档推荐的 SDK subpath。
