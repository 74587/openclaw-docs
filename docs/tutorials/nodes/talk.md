---
title: "Talk Mode 对话模式"
sidebarTitle: "对话模式"
description: "OpenClaw Nodes：Talk Mode 是连续语音对话流程，包含听、转写、模型回复和语音播放。"
---

# Talk Mode 对话模式

Talk Mode 是连续语音对话。
它不是发一条语音消息就结束，而是像打电话一样：听你说、等你停顿、发给模型、再把回复读出来。

---

## 基本流程

1. 监听语音。
2. 检测你说完了。
3. 把语音转成文字。
4. 发给主会话里的 Agent。
5. 等模型回复。
6. 用配置好的 TTS 读出来。

---

## 常见配置

```json5
{
  talk: {
    provider: "elevenlabs",
    speechLocale: "zh-CN",
    silenceTimeoutMs: 1500,
    interruptOnSpeech: true,
  },
}
```

常见字段：

- `provider`：语音播放提供商
- `speechLocale`：语音识别语言
- `silenceTimeoutMs`：停顿多久算说完
- `interruptOnSpeech`：你插话时是否打断播放

---

## 使用提醒

- 第一次先在安静环境测试。
- 如果经常提前打断，调大 `silenceTimeoutMs`。
- 如果不想被回复声音打扰，先关闭 Talk Mode。
- 语音能力通常需要麦克风和扬声器权限。

