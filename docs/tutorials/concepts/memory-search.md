---
title: "记忆搜索"
sidebarTitle: "记忆搜索"
---

# 记忆搜索：让 Agent 翻到以前写下的重点

OpenClaw 的记忆不是放在那里看的摆设。真正有用的是：当你现在问一个问题时，Agent 能把以前相关的内容找出来。

这就是记忆搜索。

---

## 一个生活例子

你曾经告诉 OpenClaw：

```text
我妈妈不能吃太甜。
```

过几天你问：

```text
帮我准备一份生日蛋糕建议。
```

好的记忆搜索应该能找回“不能吃太甜”这条信息。
这样 Agent 才不会推荐一堆高糖蛋糕。

---

## memory_search 做什么？

`memory_search` 可以按你的问题去记忆库里找相关片段，然后交给 Agent 使用。

它可能使用：

- 关键词搜索。
- 向量搜索。
- 混合搜索。
- 结果重排。

你不需要每次手动指定。OpenClaw 会根据配置选择合适方式。

---

## Embedding provider 是什么？

向量搜索需要把文字变成一串数字。这个过程叫 embedding。

OpenClaw 可以接不同的 embedding provider，例如：

- OpenAI。
- Gemini。
- Voyage。
- Mistral。
- Ollama。
- 本地模型。

选择哪个，取决于你的成本、速度、隐私要求和部署方式。

---

## 关键词搜索和语义搜索的区别

| 搜索 | 擅长 |
|------|------|
| 关键词搜索 | 找明确词语，比如订单号、文件名、人名 |
| 语义搜索 | 找意思相近的内容，比如“老人饮食”和“奶奶不能吃辣” |
| 混合搜索 | 两边都要，通常更稳 |

中文用户通常更推荐混合搜索，因为它兼顾字面和意思。

---

## 为什么有时搜不到？

常见原因：

1. 那条信息根本没有被保存成记忆。
2. 关键词太模糊。
3. embedding provider 没配置好。
4. 记忆库还没索引完成。
5. 相似度阈值太高，结果被过滤掉。

排查时可以先问自己：这条信息真的进记忆库了吗？

---

## 继续阅读

- [记忆 Memory](/tutorials/concepts/memory)
- [内置记忆引擎](/tutorials/concepts/memory-builtin)
- [QMD 记忆后端](/tutorials/concepts/memory-qmd)
- [主动记忆](/tutorials/concepts/active-memory)

