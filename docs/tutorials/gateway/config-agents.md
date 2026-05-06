---
title: "Agent 配置"
sidebarTitle: "Agent 配置"
---

# Agent 配置：决定 AI 助手怎么工作

`agents.*` 相关配置决定 Agent 的默认工作区、模型、技能、上下文文件、会话和消息行为。

你可以把它想成给助手准备工位：桌子在哪里、能看哪些说明书、能用哪些技能、一次能带多少资料。

---

## 最常见的配置

| 配置 | 作用 |
|------|------|
| `agents.defaults.workspace` | 默认工作区 |
| `agents.defaults.repoRoot` | 项目根目录提示 |
| `agents.defaults.skills` | 默认允许的技能 |
| `agents.defaults.contextInjection` | 是否注入工作区说明文件 |
| `agents.list` | 配多个 Agent |
| `multiAgent` | 多 Agent 路由 |
| `session` | 会话生命周期和绑定 |
| `messages` | 消息投递和格式 |
| `talk` | 语音/对话模式相关配置 |

---

## 工作区

默认工作区通常是：

```text
~/.openclaw/workspace
```

示意配置：

```json5
{
  agents: {
    defaults: {
      workspace: "~/.openclaw/workspace"
    }
  }
}
```

工作区里常见 `AGENTS.md`、`SOUL.md`、`USER.md` 等文件。它们会影响 Agent 的规则、风格和记忆。

---

## 技能 allowlist

如果你想限制 Agent 能用哪些技能，可以配置：

```json5
{
  agents: {
    defaults: {
      skills: ["github", "weather"]
    },
    list: [
      { id: "writer" },
      { id: "locked-down", skills: [] }
    ]
  }
}
```

意思是：

- `writer` 继承默认技能。
- `locked-down` 不允许任何技能。
- 单个 Agent 设置了自己的 skills，就以它自己的为准。

---

## 上下文注入

`contextInjection` 决定工作区说明文件什么时候进入系统提示词。

常见值：

| 值 | 说明 |
|----|------|
| `always` | 每次都注入 |
| `continuation-skip` | 安全续写时跳过，省上下文 |
| `never` | 完全不注入，适合自定义 runtime |

新手保持默认即可。

---

## 配多个 Agent

你可以让不同 Agent 有不同工作区、工具和风格。例如：

- `main` 负责日常聊天。
- `docs` 负责写文档。
- `ops` 负责运维检查。

多 Agent 很强，但配置也更复杂。基础通道和模型没跑稳前，不建议一开始就拆很多 Agent。

---

## Talk 配置

`talk` 控制语音对话。
它分两层：

- `talk.provider` + `talk.providers.<provider>`：传统语音播放，也就是 `talk.speak` 和 STT/TTS 模式里的 TTS。
- `talk.realtime.*`：浏览器或服务端实时语音会话。

示例：

```json5
{
  talk: {
    provider: "elevenlabs",
    speechLocale: "zh-CN",
    silenceTimeoutMs: 1500,
    interruptOnSpeech: true,
    realtime: {
      provider: "openai",
      providers: {
        openai: {
          model: "gpt-realtime",
          voice: "alloy"
        }
      },
      mode: "realtime",
      transport: "webrtc",
      brain: "agent-consult"
    }
  }
}
```

如果配置里还写着旧字段：

- `talk.mode`
- `talk.transport`
- `talk.brain`
- `talk.model`
- `talk.voice`

运行：

```bash
openclaw doctor --fix
```

新版 doctor 会把这些旧的顶层 realtime selector 迁到 `talk.realtime`。

---

## 继续阅读

- [Agent 是什么](/tutorials/concepts/agent)
- [多智能体路由](/tutorials/concepts/multi-agent)
- [SOUL.md](/tutorials/concepts/soul)
