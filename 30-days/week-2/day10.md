# 第 10 天：Attention 机制——让模型学会"看哪里"

> 💡 **今天只需要 15 分钟就能完成最小版本**  
> 论文：*Neural Machine Translation by Jointly Learning to Align and Translate*（Bahdanau et al., 2015）

---

## 📋 今日概览

Attention 机制是 Transformer 的前身，是现代深度学习最重要的思想之一。  
理解了 Bahdanau Attention，你就理解了 Transformer 的 90% 核心思想。

今天你要搞清楚：**Seq2Seq 有什么问题？Attention 是怎么解决的？Attention 和"加权求和"的关系？**

---

## ⏱️ 最小启动版本（15 分钟）

```
请讲解 Attention 机制（Bahdanau Attention）：
1. Seq2Seq 的信息瓶颈问题是什么
2. Attention 的核心思想：每一步解码时，动态关注输入的不同部分
3. Attention 的计算步骤（对齐分数 → softmax → 加权求和）
4. Attention 和"加权求和"的关系
5. 面试 1 分钟回答模板
```

填写论文卡必填 5 项。完成！

---

## 🚀 完整版任务（30 分钟）

### 步骤 1：间隔复习（3 分钟）

不看笔记回忆：
- 残差连接的公式？（Day 9）
- Word2Vec 的负采样解决了什么？（Day 5）

### 步骤 2：AI 速读（10 分钟）

使用上方提示词。追问：

```
请解释：
1. Attention 的 Query、Key、Value 各是什么（先用 Bahdanau Attention 解释，再说明 Transformer 怎么扩展）
2. Soft Attention vs Hard Attention 的区别
3. Self-Attention 和 Cross-Attention 的区别
```

### 步骤 3：理解核心概念（8 分钟）

**Seq2Seq 的问题：**
- 编码器把整个输入序列压缩成一个固定长度的向量（context vector）
- 长句子信息会丢失
- 解码器的每一步都用同一个 context vector

**Attention 的解法：**
```
1. 编码器输出每个时间步的 hidden state：h₁, h₂, ..., hₙ
2. 对每个解码时间步，计算对每个 hᵢ 的"对齐分数"
3. 用 softmax 把分数变成权重
4. 加权求和，得到这一步的 context vector
```

**Attention 的直觉：**
- 翻译"bank"这个词时，模型会把更多注意力放在输入中"bank"的位置
- 而不是对所有输入一视同仁

**为什么叫 Query/Key/Value？（为明天的 Transformer 做铺垫）**
- Query：解码器当前步的 hidden state（"我想找什么"）
- Key：编码器每步的 hidden state（"我有什么"）
- Value：和 Key 相关联的内容（"给你的信息"）

### 步骤 4：填完整论文卡（5 分钟）

### 步骤 5：主动回忆（4 分钟）

1. Attention 的 3 步计算是什么？
2. Q/K/V 分别代表什么含义？
3. Self-Attention 和 Cross-Attention 的区别？

---

## ✅ 完成标准

- [ ] 能解释 Seq2Seq 的信息瓶颈问题
- [ ] 能说出 Attention 的 3 步计算
- [ ] 能解释 Q/K/V 的含义
- [ ] 准备好迎接明天的 Transformer

---

## 🤖 今日 AI 提示词

### 提示词 1：速读
```
请讲解 Attention 机制（从 Bahdanau Attention 开始）：
1. Seq2Seq 的信息瓶颈
2. Attention 的 3 步计算（对齐 → softmax → 加权求和）
3. Q/K/V 的含义（先 Bahdanau，再 Transformer 版本）
4. Self-Attention vs Cross-Attention
5. 面试 1 分钟回答
```

### 提示词 2：形象化理解
```
请用"图书馆查找"的比喻解释 Attention 机制中的 Query、Key、Value：
- Query 是什么（搜索请求）
- Key 是什么（书目索引）
- Value 是什么（书的内容）
- Attention 分数是什么（相关性得分）
```

### 提示词 3：面试题
```
出 3 道面试题考我 Attention 机制，然后等我回答后纠错：
1. 概念题：Attention 解决了什么问题
2. 原理题：请解释 Attention 的计算过程
3. 对比题：Self-Attention 和 Cross-Attention 的区别是什么
```

---

## 🍱 可选加餐

- 了解 **Scaled Dot-Product Attention**（Transformer 用的版本）
- 了解 **Multi-Head Attention** 为什么要用多个头
- 画一张图，展示 Attention 的计算流程

---

## 🆘 卡住了怎么办

**"Q/K/V 搞不清楚"**  
→ 先忘掉这 3 个字母，记住核心：Attention 就是"对每个输入元素计算一个权重，然后加权求和"

**"Self-Attention 是什么"**  
→ 明天学 Transformer 时会详细讲。今天只需要知道：Self-Attention = 输入和自己做 Attention

---

[← Day 9](day09.md) | [返回总览](../README.md) | [Day 11 →](day11.md)
