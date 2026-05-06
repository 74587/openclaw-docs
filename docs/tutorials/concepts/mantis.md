---
title: "Mantis QA"
sidebarTitle: "Mantis QA"
---

# Mantis QA：真实通道问题的前后验证

Mantis 是维护者用于验证真实通道 bug 的 QA 路线。它关注“修复前是什么样、修复后是不是真的好了”。

普通用户可以跳过这一页。

---

## 它适合什么？

适合维护者排查：

- Discord 状态反应是否正确。
- Slack in VNC 是否正常。
- 桌面或浏览器冒烟是否通过。
- 某个 live transport bug 是否复现并修复。

---

## 为什么需要 Mantis？

很多通道问题不是单元测试能完全覆盖的。
真实聊天平台有权限、延迟、消息格式、附件、反应、线程等复杂行为。

Mantis 的价值是把“我感觉修好了”变成“有前后证据”。

---

## 新手理解

它不是普通安装功能。
它是 OpenClaw 维护者的测试工具。

---

## 继续阅读

- [QA 自动化](/tutorials/concepts/qa-e2e-automation)
- [Matrix QA](/tutorials/concepts/qa-matrix)
- [QA 测试通道](/tutorials/channels/qa-channel)

