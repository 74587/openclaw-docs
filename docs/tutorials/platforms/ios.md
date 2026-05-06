---
title: "iOS"
sidebarTitle: "iOS"
---

# iOS：作为 OpenClaw Node 接入

iOS App 的定位是 Node，不是 Gateway。它连接到已有 Gateway，然后提供手机能力。

可能能力：

- Canvas。
- 摄像头。
- 屏幕快照。
- 位置。
- Talk 模式。
- Voice wake。

基本流程：

1. 在电脑或服务器启动 Gateway。
2. iOS App 发现或手动连接 Gateway。
3. 在 Gateway 侧批准配对。
4. 用 `openclaw nodes status` 检查连接。

继续阅读：[节点入门](/tutorials/nodes/)。

