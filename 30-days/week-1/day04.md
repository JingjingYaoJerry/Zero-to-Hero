# 第 4 天：Batch Normalization——让深层网络训练变稳定的秘密

> 💡 **今天只需要 15 分钟就能完成最小版本**  
> 论文：*Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift*（Ioffe & Szegedy, 2015）

---

## 📋 今日概览

你在代码里写过 `nn.BatchNorm2d(64)` 吗？  
今天你要搞清楚：**BN 是怎么工作的？为什么它能加快训练？它和 LayerNorm 的区别是什么？**

BN vs LN 是**高频面试题**，今天把这道题彻底搞定。

**今天额外任务：复习 Day 3 的 Dropout（1 分钟口述）**

---

## ⏱️ 最小启动版本（15 分钟）

**步骤 1（10 分钟）：AI 速读**

```
请讲解 Batch Normalization：
1. 它解决了什么问题（Internal Covariate Shift 是什么）
2. BN 的计算步骤（normalize → scale → shift）
3. 训练时和推理时的行为差异
4. 为什么 BN 有 gamma 和 beta 这两个可学习参数
5. BN 和 LayerNorm 的区别（一定要讲清楚，这是面试高频题）
6. 面试 1 分钟回答模板
```

**步骤 2（5 分钟）：填论文卡必填 5 项**

> 🎉 **完成！**

---

## 🚀 完整版任务（30 分钟）

### 步骤 1：间隔复习（2 分钟）

快速回忆昨天的 Dropout（不看笔记）：  
→ Dropout 训练 vs 推理的行为差异是什么？

### 步骤 2：AI 速读（10 分钟）

使用上方提示词。追问：

```
请解释：为什么 BN 在小 batch size 下效果会变差？
以及：为什么 Transformer 用 LayerNorm 而不是 BatchNorm？
```

### 步骤 3：理解 BN 的关键机制（8 分钟）

**BN 的 4 步计算（每个 mini-batch 内）：**
```
1. 计算均值：μ = mean(x)
2. 计算方差：σ² = var(x)  
3. 归一化：x_norm = (x - μ) / √(σ² + ε)
4. 缩放平移：y = γ * x_norm + β
```

**训练 vs 推理的区别：**
- 训练时：用当前 batch 的均值和方差
- 推理时：用训练过程中积累的**移动平均**均值和方差

**BN vs LN（记住这张表）：**

| | BatchNorm | LayerNorm |
|---|---|---|
| 归一化维度 | 在 batch 维度上 | 在特征维度上 |
| 适合 | CNN、固定 batch 大小 | Transformer、RNN、小 batch |
| batch size 影响 | 有（小 batch 效果差） | 无 |
| 常见场景 | 图像分类、CNN | NLP、Transformer |

### 步骤 4：完整填写论文卡（5 分钟）

### 步骤 5：主动回忆（5 分钟）

合上笔记：
1. BN 的 4 步计算是什么？
2. BN 推理时用什么均值方差？
3. 为什么 Transformer 用 LN 不用 BN？

---

## ✅ 完成标准

- [ ] 能说出 BN 的 4 步计算流程
- [ ] 能说清楚 BN 训练 vs 推理的差异
- [ ] 能回答"BN 和 LN 的区别"这道面试题
- [ ] 连续 3 天的论文卡都已填好

---

## 🤖 今日 AI 提示词

### 提示词 1：速读
```
请讲解 Batch Normalization：
1. 解决的问题
2. 计算步骤（4 步）
3. 训练 vs 推理的差异
4. 为什么有 gamma 和 beta
5. BN vs LN vs InstanceNorm vs GroupNorm 的区别表格
6. 面试 1 分钟回答
```

### 提示词 2：面试题练习
```
请出这些面试题，我来回答，你来纠错：
1. BN 是什么，解决了什么问题？
2. BN 在训练和推理时有什么区别？
3. 为什么 Transformer 不用 BN 用 LN？
4. BN 在 batch size 很小时会有什么问题？
5. Dropout 和 BN 一起用会有什么问题？
```

### 提示词 3：工程理解
```
从工程角度，帮我解释：
1. 在 PyTorch 里，BN 的 momentum 参数是什么含义
2. model.eval() 会对 BN 做什么
3. 如果忘记在推理时调用 model.eval()，BN 会怎样（会有什么 bug）
```

---

## 🍱 可选加餐

- 了解 **Layer Normalization、Instance Normalization、Group Normalization** 四种 Norm 的区别
- 写一个最小 BN 实现（用 numpy）
- 了解 **Pre-LN vs Post-LN**（Transformer 里 BN 放在哪里的争论）

---

## 🆘 卡住了怎么办

**"Internal Covariate Shift 搞不清楚"**  
→ 忽略这个术语，只记住："BN 让每层的输入分布更稳定，所以训练更快"

**"BN 和 LN 记不清楚"**  
→ 只记住一句话：BN 在 batch 上算，LN 在每个样本的特征上算

**"gamma 和 beta 的作用不明白"**  
→ 问 AI："如果没有 gamma 和 beta，BN 会有什么问题"

---

## 📌 明天预告

**Day 5：Word2Vec——词向量是怎么"学"出来的**

---

[← Day 3](day03.md) | [返回总览](../README.md) | [Day 5 →](day05.md)
