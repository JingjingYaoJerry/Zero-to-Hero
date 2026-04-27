# 第 16 天：GPT 思想——自回归生成的魔力

> 💡 **今天只需要 15 分钟就能完成最小版本**  
> 核心：GPT 系列的设计思想（GPT-1 / GPT-2 / GPT-3 的演进逻辑）

---

## 📋 今日概览

GPT 是 ChatGPT 的前身，也是当前大语言模型（LLM）的核心架构。  
今天你要搞清楚：**GPT 和 BERT 的根本差异、为什么 GPT 适合生成、"规模就是一切"的思想**

---

## ⏱️ 最小启动版本（15 分钟）

```
请讲解 GPT 系列的设计思想：
1. GPT 的预训练任务是什么（自回归语言模型）
2. GPT（Decoder-only）和 BERT（Encoder-only）的根本区别
3. GPT-1 → GPT-2 → GPT-3 的演进逻辑（规模化）
4. In-Context Learning（情境学习）是什么
5. 面试 2 分钟回答模板
```

填写论文卡必填 5 项。完成！

---

## 🚀 完整版任务（35 分钟）

### 步骤 1：间隔复习（3 分钟）

不看笔记：BERT 的两个预训练任务是什么？输入由哪 3 种嵌入组成？

### 步骤 2：AI 速读（12 分钟）

使用上方提示词。追问：

```
请深化解释：
1. Causal Attention（Masked Self-Attention）在 GPT 中的作用
2. GPT-3 的 few-shot、one-shot、zero-shot 的区别
3. Prompt Engineering 是什么，为什么 GPT 系列需要这个
4. 为什么 GPT 不需要 Fine-tuning（相比 BERT）
```

### 步骤 3：理解核心概念（12 分钟）

**GPT 的训练任务：自回归语言模型**
```
给定前面的词，预测下一个词
P(token_t | token_1, ..., token_{t-1})
只看左边的上下文（单向）
```

**GPT vs BERT 对比（重点记忆）：**

| | BERT | GPT |
|---|---|---|
| 结构 | Encoder-only | Decoder-only |
| 预训练任务 | 完形填空（MLM）| 预测下一个词 |
| 注意力方向 | 双向 | 单向（只看左边）|
| 适合任务 | 理解（分类、QA）| 生成（对话、写作）|
| 使用方式 | 预训练 + 微调 | 预训练 + Prompt |

**GPT 规模化的演进：**
```
GPT-1（2018）：1.17 亿参数，证明预训练有效
GPT-2（2019）：15 亿参数，生成质量震惊社区
GPT-3（2020）：1750 亿参数，in-context learning 惊现
ChatGPT（2022）：GPT-3.5 + RLHF，对话能力爆发
GPT-4（2023）：多模态，能力大幅提升
```

**In-Context Learning 的核心直觉：**
- 模型足够大时，你只需要给几个例子，它就能"举一反三"
- 不需要更新参数，不需要微调
- 这是 GPT-3 带来的范式转变

### 步骤 4：填完整论文卡（5 分钟）

### 步骤 5：主动回忆（3 分钟）

1. GPT 和 BERT 的根本区别（结构 + 预训练任务 + 适合任务）？
2. In-Context Learning 是什么？
3. GPT 系列规模化的演进是什么？

---

## ✅ 完成标准

- [ ] 能清楚说出 GPT 和 BERT 的 3 个主要区别
- [ ] 能解释 In-Context Learning
- [ ] 能说出 GPT-1 到 GPT-3 的演进逻辑
- [ ] 能回答"为什么大模型不需要微调就能做任务"

---

## 🤖 今日 AI 提示词

### 提示词 1：速读
```
请讲解 GPT 系列：
1. 自回归语言模型的训练任务
2. Decoder-only 架构（Masked Self-Attention）
3. GPT-1 → GPT-3 的演进
4. In-Context Learning（zero-shot、one-shot、few-shot）
5. 为什么 GPT 适合生成任务
6. 面试 2 分钟回答
```

### 提示词 2：BERT vs GPT 深化
```
请帮我彻底搞清楚 BERT 和 GPT 的区别：
1. 结构上的区别（Encoder vs Decoder）
2. 注意力的区别（双向 vs 单向）
3. 预训练任务的区别
4. 下游使用方式的区别
5. 各自最适合的任务类型
6. 结合 T5 解释 Encoder-Decoder 的优势
```

### 提示词 3：LLM 演进
```
请帮我梳理从 BERT/GPT 到现代大语言模型（LLM）的发展路径：
GPT-3 → InstructGPT → ChatGPT → GPT-4
以及：RLHF 是什么，为什么它对大模型的对话能力至关重要
```

---

## 🍱 可选加餐

- 了解 **InstructGPT**（GPT + RLHF 的结合）
- 了解 **Llama / Llama 2**（开源 GPT 系列）
- 尝试用 GPT-3.5 API 写一个 few-shot 学习示例

---

## 🆘 卡住了怎么办

**"Decoder-only 架构不理解"**  
→ 记住：Decoder-only = 每个 token 只看它左边的 token，不看右边。这让模型可以一个一个词地生成文本

**"In-Context Learning 不理解"**  
→ 记住：给模型几个例子（"问：X，答：Y"），然后问它一个新问题，它就能照着回答。不需要改模型参数

---

[← Day 15](day15.md) | [返回总览](../README.md) | [Day 17 →](day17.md)
