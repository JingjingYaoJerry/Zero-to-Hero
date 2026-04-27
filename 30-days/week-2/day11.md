# 第 11 天：Transformer——改变 AI 的架构

> 💡 **今天只需要 15 分钟就能完成最小版本**  
> 论文：*Attention Is All You Need*（Vaswani et al., 2017）

---

## 📋 今日概览

Transformer 是过去 10 年 AI 最重要的发明，BERT、GPT、ChatGPT 都建立在它之上。  
今天你要搞清楚：**Transformer 的整体结构 + Self-Attention 的计算 + 为什么它比 RNN 好**

这一天内容比较多，建议至少完成最小版本，完整版分 2 天也没关系。

---

## ⏱️ 最小启动版本（15 分钟）

```
请讲解 Transformer 架构（Attention Is All You Need）：
1. Transformer 的整体结构（Encoder + Decoder）
2. Self-Attention 的计算步骤（Q/K/V 的矩阵计算）
3. Multi-Head Attention 是什么，为什么要多个头
4. Positional Encoding 是什么，为什么需要它
5. 为什么 Transformer 比 RNN/LSTM 更好（并行化 + 长距离依赖）
6. 面试 2 分钟回答模板
```

填写论文卡必填 5 项。完成！

---

## 🚀 完整版任务（45 分钟）

### 步骤 1：间隔复习（3 分钟）

不看笔记：Attention 的 Q/K/V 分别是什么？

### 步骤 2：AI 速读（15 分钟）

使用上方提示词。追问：

```
请进一步解释：
1. Scaled Dot-Product Attention 为什么要除以 √d_k（防止梯度消失的作用）
2. Transformer 的 Feed-Forward Network 在哪里，作用是什么
3. Layer Normalization 在 Transformer 里放在哪里（Pre-LN vs Post-LN）
4. 编码器的 Self-Attention 和解码器的 Cross-Attention 有什么区别
```

### 步骤 3：理解关键结构（15 分钟）

**Transformer Encoder 的一层（6 层叠加）：**
```
输入 →
  Multi-Head Self-Attention →
  Add & Norm（残差 + LayerNorm）→
  Feed-Forward Network →
  Add & Norm →
输出
```

**Self-Attention 的计算：**
```
1. Q = XW_Q, K = XW_K, V = XW_V（线性投影）
2. 对齐分数 = QK^T / √d_k
3. 权重 = softmax(对齐分数)
4. 输出 = 权重 × V
```

**为什么比 RNN 好：**

| | RNN/LSTM | Transformer |
|---|---|---|
| 并行化 | ❌ 顺序计算 | ✅ 并行计算 |
| 长距离依赖 | ❌ 路径长，梯度消失 | ✅ 任意两词直接 attention |
| 训练速度 | 慢 | 快 |
| 参数效率 | 中等 | 高 |

**Positional Encoding 的作用：**
- Transformer 的 Attention 没有位置概念（全是并行的）
- 需要人为加入位置信息：`sin/cos(position, dimension)`
- 或者用可学习的位置嵌入（BERT 用这个）

### 步骤 4：填完整论文卡（8 分钟）

**重点填写（这是高频面试内容）：**
- 方法概览（Encoder + Decoder 结构）
- 关键公式（Self-Attention 计算）
- Transformer vs RNN 对比
- 面试表达版

### 步骤 5：主动回忆（4 分钟）

1. Transformer Encoder 一层的结构是什么（4 个步骤）？
2. Self-Attention 的计算是什么（4 步）？
3. 为什么要 Scale（除以 √d_k）？
4. Positional Encoding 为什么需要？

---

## ✅ 完成标准

- [ ] 能说出 Transformer Encoder 的每一层结构
- [ ] 能解释 Self-Attention 的计算步骤
- [ ] 能回答"Transformer 比 RNN 好在哪里"
- [ ] 能解释 Positional Encoding 的作用

---

## 🤖 今日 AI 提示词

### 提示词 1：速读
```
请讲解 Transformer（Attention Is All You Need）：
1. 整体架构（Encoder + Decoder + 各层组件）
2. Self-Attention 计算步骤（矩阵形式）
3. Multi-Head Attention 的作用
4. Positional Encoding
5. 为什么比 RNN 好
6. 面试 2 分钟回答框架
```

### 提示词 2：结构画图
```
请用 ASCII 图画出 Transformer Encoder 的一层结构，
标注出：输入、Multi-Head Self-Attention、Add&Norm、FFN、输出
```

### 提示词 3：深度追问
```
请解释这些 Transformer 的细节：
1. 为什么 Scale 除以 √d_k（不除会有什么问题）
2. Multi-Head 的每个 head 会学到什么（直觉）
3. FFN（Feed-Forward Network）里的两层线性层学到了什么
4. Pre-LN vs Post-LN 哪个更好，为什么
```

### 提示词 4：面试准备
```
面试题：请解释 Transformer 的 Self-Attention 机制，以及它为什么能处理长距离依赖。
帮我出满分答题框架（含公式、直觉解释、与 RNN 对比）。
```

---

## 🍱 可选加餐

- 手写 Self-Attention 的 numpy 实现（矩阵计算，10 行以内）
- 了解 **Encoder-only（BERT）vs Decoder-only（GPT）vs Encoder-Decoder（T5）** 的差异
- 阅读 Jay Alammar 的 Transformer 图解文章（搜索"The Illustrated Transformer"）

---

## 🆘 卡住了怎么办

**"结构太复杂，记不住"**  
→ 只记住 3 个组件：Self-Attention + 残差连接 + LayerNorm。其他都是细节。

**"Q/K/V 的矩阵计算搞不清楚"**  
→ 问 AI："请用一个 3 个词的句子，手动演算一遍 Self-Attention 的计算过程"

**"Multi-Head 不理解"**  
→ 只记住：多个头 = 从多个角度看输入，然后把结果拼起来

---

## 📌 明天预告

**Day 12：SVM——理解支持向量机，搞定传统 ML 面试**

---

[← Day 10](day10.md) | [返回总览](../README.md) | [Day 12 →](day12.md)
