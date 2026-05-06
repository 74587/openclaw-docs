---
title: "Memory Config"
sidebarTitle: "记忆配置"
---

# Memory Config

记忆配置决定 OpenClaw 如何保存、搜索和注入长期信息。

常见选择：

- 内置 SQLite 记忆。
- QMD 本地资料后端。
- Honcho 或外部记忆服务。
- Dreaming 后台整理。

继续阅读：[记忆 Memory](/tutorials/concepts/memory)。

## 新手怎么选

个人使用先用内置记忆，不要一开始就接复杂外部服务。
团队知识库多、数据量大、需要更强检索时，再考虑 QMD、Wiki 或外部后端。

配置后先检查：

```bash
openclaw memory status --deep
openclaw doctor
```
