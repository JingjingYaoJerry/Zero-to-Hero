# 第 15 天：BERT——预训练语言模型的里程碑

> 💡 **今天只需要 15 分钟就能完成最小版本**  
> 论文：*BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding*（Devlin et al., 2019）

---

## 📋 今日概览

BERT 是 NLP 的 ImageNet 时刻：**一个预训练模型，微调就能解决几乎所有 NLP 任务**。  
今天你要搞清楚：**BERT 是怎么训练的、为什么它是"双向"的、它和 GPT 的根本区别**

---

## ⏱️ 最小启动版本（15 分钟）

```
请讲解 BERT：
1. BERT 的预训练任务是什么（MLM 和 NSP）
2. 为什么叫"双向"，和 GPT 的单向自回归有什么区别
3. BERT 的微调（Fine-tuning）范式是什么
4. BERT 的输入格式（[CLS]、[SEP]、segment embedding）
5. 面试 2 分钟回答模板
```

填写论文卡必填 5 项。完成！

---

## 🚀 完整版任务（35 分钟）

### 步骤 1：间隔复习（3 分钟）

不看笔记：
- Transformer Encoder 的一层结构？（Day 11）
- XGBoost 和随机森林的最大区别？（Day 13）

### 步骤 2：AI 速读（12 分钟）

使用上方提示词。追问：

```
请深化解释：
1. MLM（Masked Language Model）的具体做法（15% 的 token 如何处理）
2. 为什么 NSP（Next Sentence Prediction）后来被发现不是必要的（RoBERTa 结论）
3. BERT 的 [CLS] token 有什么特殊作用
4. BERT 的词嵌入是如何构成的（Token + Position + Segment）
```

### 步骤 3：理解核心概念（12 分钟）

**BERT 的两阶段训练范式：**
```
阶段 1：预训练（Pretraining）
→ 在大量无标注文本上训练
→ 任务 1：MLM（完形填空）
→ 任务 2：NSP（下一句预测）

阶段 2：微调（Fine-tuning）
→ 在具体任务的标注数据上训练
→ 在 BERT 上加一个小的任务头（如分类层）
→ 只需要少量数据就能达到很好效果
```

**为什么"双向"很重要：**
- GPT：只看左边的上下文（左到右，自回归）
- BERT：同时看左边和右边的上下文（双向，完形填空式）
- 双向让 BERT 的表示更丰富，适合理解任务

**BERT 的 4 种输入嵌入（相加）：**
```
Token Embedding：词本身的嵌入
Position Embedding：可学习的位置嵌入（不是 sin/cos）
Segment Embedding：区分第一句（A）还是第二句（B）
最终输入 = Token + Position + Segment
```

**BERT 的关键超参数：**
- BERT-base：12 层，768 维，12 个 attention head，1.1 亿参数
- BERT-large：24 层，1024 维，16 个 attention head，3.4 亿参数

### 步骤 4：填完整论文卡（5 分钟）

**重点填写：**
- BERT vs GPT 对比
- 微调范式的说明
- 面试表达版（你能回答哪些问题）

### 步骤 5：主动回忆（3 分钟）

1. BERT 的两个预训练任务是什么？
2. 为什么 BERT 是双向的？
3. BERT 的输入由哪 3 种嵌入组成？

---

## ✅ 完成标准

- [ ] 能解释 MLM 和 NSP 的训练任务
- [ ] 能说清楚 BERT 和 GPT 的根本区别
- [ ] 能解释 BERT 的微调范式
- [ ] 能回答"BERT 的输入格式是什么"

---

## 🤖 今日 AI 提示词

### 提示词 1：速读
```
请讲解 BERT：
1. 预训练任务（MLM + NSP）
2. 双向 vs 单向（和 GPT 的根本区别）
3. 微调范式（Fine-tuning）
4. 输入格式（3 种嵌入）
5. BERT 的局限性
6. 面试 2 分钟回答
```

### 提示词 2：对比
```
请做一张对比表：BERT vs GPT vs T5
对比维度：
- 结构（Encoder-only / Decoder-only / Encoder-Decoder）
- 预训练任务
- 适合的下游任务
- 特点
```

### 提示词 3：面试题
```
面试题：
1. BERT 的预训练任务是什么，为什么这样设计？
2. 为什么 BERT 适合理解任务但不适合生成任务？
3. BERT 和 GPT 的根本区别是什么？
4. 什么是 RoBERTa，它和 BERT 的区别是什么？

请出这 4 题，我来回答，你来纠错和补充。
```

---

## 🍱 可选加餐

- 了解 **RoBERTa**（BERT 的优化版：更多数据 + 去掉 NSP）
- 了解 **DistilBERT**（BERT 的蒸馏版：更小更快）
- 用 HuggingFace transformers 加载 BERT 并做一个情感分类任务（5 行代码）：
  ```python
  from transformers import pipeline
  classifier = pipeline("sentiment-analysis")
  result = classifier("I love machine learning!")
  ```

---

## 🆘 卡住了怎么办

**"MLM 搞不清楚"**  
→ 记住：MLM = 完形填空，把句子里 15% 的词盖住，让模型猜出来

**"为什么双向更好"**  
→ 理解一个词需要它左边和右边的上下文，比如"我去银行取钱"中"银行"的意思，需要"取钱"来确认

**"微调范式不清楚"**  
→ 记住：预训练 = 学通识，微调 = 学专科。BERT 先学语言通识，然后在具体任务上学专科

---

## 📌 明天预告

**Day 16：GPT 思想——生成式预训练的魔力**

---

[← Day 14](../week-2/day14.md) | [返回总览](../README.md) | [Day 16 →](day16.md)
