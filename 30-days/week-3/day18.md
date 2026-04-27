# 第 18 天：最小复现练习——动手才能真正记住

> 💡 **今天只需要 20 分钟就能完成最小版本**  
> 今天不读新论文，选一篇已学论文做最小可运行复现

---

## 📋 今日概览

复现是最强的记忆方式。你读过 10 篇论文，不如复现 1 篇记得牢。  
今天的目标：**写出 20-30 行代码，验证你真正理解了某个核心机制**

不需要完整复现论文，只需要实现一个关键模块。

---

## 🎯 选择你的复现目标

### 🟢 难度 1（推荐）：实现一个最简 Attention 计算

```python
import torch
import torch.nn.functional as F

def simple_attention(Q, K, V, d_k):
    """
    Q: [batch, seq_len, d_k]
    K: [batch, seq_len, d_k]
    V: [batch, seq_len, d_v]
    """
    # 1. 计算对齐分数
    scores = torch.bmm(Q, K.transpose(1, 2)) / (d_k ** 0.5)
    
    # 2. Softmax 归一化
    weights = F.softmax(scores, dim=-1)
    
    # 3. 加权求和
    output = torch.bmm(weights, V)
    return output, weights

# 测试
batch, seq_len, d_k = 2, 5, 64
Q = torch.randn(batch, seq_len, d_k)
K = torch.randn(batch, seq_len, d_k)
V = torch.randn(batch, seq_len, d_k)

output, weights = simple_attention(Q, K, V, d_k)
print(f"Output shape: {output.shape}")
print(f"Attention weights sum: {weights.sum(dim=-1)}")  # 应该全是 1
```

### 🟡 难度 2：实现一个简单的残差块（ResNet Block）

```python
import torch
import torch.nn as nn

class ResidualBlock(nn.Module):
    def __init__(self, channels):
        super().__init__()
        self.conv1 = nn.Conv2d(channels, channels, 3, padding=1)
        self.bn1 = nn.BatchNorm2d(channels)
        self.conv2 = nn.Conv2d(channels, channels, 3, padding=1)
        self.bn2 = nn.BatchNorm2d(channels)
        self.relu = nn.ReLU()
    
    def forward(self, x):
        residual = x  # 保存输入（identity）
        
        out = self.relu(self.bn1(self.conv1(x)))
        out = self.bn2(self.conv2(out))
        
        out = out + residual  # 残差连接
        out = self.relu(out)
        return out

# 测试
block = ResidualBlock(channels=64)
x = torch.randn(4, 64, 32, 32)  # batch=4, channels=64, 32x32
out = block(x)
print(f"Input: {x.shape}, Output: {out.shape}")  # 形状不变
```

### 🔴 难度 3：实现带 Dropout 和 BatchNorm 的小型分类网络

```python
import torch
import torch.nn as nn

class SmallClassifier(nn.Module):
    def __init__(self, input_dim=784, hidden_dim=256, num_classes=10):
        super().__init__()
        self.network = nn.Sequential(
            nn.Linear(input_dim, hidden_dim),
            nn.BatchNorm1d(hidden_dim),  # BatchNorm
            nn.ReLU(),
            nn.Dropout(p=0.5),           # Dropout
            nn.Linear(hidden_dim, hidden_dim // 2),
            nn.BatchNorm1d(hidden_dim // 2),
            nn.ReLU(),
            nn.Dropout(p=0.3),
            nn.Linear(hidden_dim // 2, num_classes)
        )
    
    def forward(self, x):
        return self.network(x)

# 测试
model = SmallClassifier()
x = torch.randn(32, 784)  # batch=32
output = model(x)
print(f"Output shape: {output.shape}")  # [32, 10]

# 训练 vs 推理模式的差异
model.train()
out_train = model(x)
model.eval()
out_eval = model(x)
print(f"训练/推理输出是否相同: {torch.allclose(out_train, out_eval)}")  # False（因为 Dropout）
```

---

## ⏱️ 最小启动版本（20 分钟）

1. 选一个难度级别（建议从难度 1 或 2 开始）
2. 把代码粘贴到 Jupyter Notebook 或 Python 文件里
3. 运行，看输出是否符合预期
4. 修改 1 个参数（比如改 d_k，改 channels），重新运行，观察变化

> 如果代码报错了，把错误信息发给 AI，请它帮你 debug。

---

## 🚀 完整版任务（45 分钟）

### 步骤 1：运行最小复现（20 分钟）

选一个难度，把代码跑通，确认理解每一行的含义。

### 步骤 2：用 AI 深化理解（15 分钟）

把你实现的代码发给 AI，问：

```
我实现了这段代码，请帮我：
1. 指出代码中体现了论文哪些核心概念
2. 告诉我这个实现哪些地方简化了（和论文的完整实现有什么差异）
3. 给我出 3 道关于这段代码的问题考我
4. 告诉我下一步可以如何扩展这个实现
```

### 步骤 3：记录踩坑（5 分钟）

在错题本里记录：
- 你遇到的错误是什么
- 为什么会出现这个错误
- 解决方法是什么

### 步骤 4：更新论文卡（5 分钟）

在对应论文卡的"工程视角"部分，添加你的复现笔记：
- 实现了哪个关键模块
- 遇到了什么问题
- 通过实现加深了哪些理解

---

## ✅ 完成标准

- [ ] 代码能运行，输出正确（至少一个难度级别）
- [ ] 能解释代码每一行的含义
- [ ] 错题本里记录了至少 1 个踩坑点

---

## 🤖 今日 AI 提示词

### Debug 提示词
```
我在复现 [Attention / ResNet / Dropout+BN] 时遇到了以下错误：
[粘贴错误信息]
代码如下：
[粘贴代码]
请帮我 debug，并解释错误原因。
```

### 深化理解提示词
```
我实现了以下代码：
[粘贴代码]
请帮我：
1. 指出哪些地方体现了原论文的核心思想
2. 哪些地方是我的简化
3. 如果要做一个完整复现，还需要加什么
```

---

## 🍱 可选加餐

- 把难度 1、2、3 都跑通
- 在真实数据上（MNIST）跑 SmallClassifier，观察加 Dropout/BN 前后的训练曲线差异
- 实现 Multi-Head Attention（在 simple_attention 基础上扩展）

---

## 🆘 卡住了怎么办

**"代码报错，看不懂"**  
→ 把完整错误信息粘贴给 AI，让它帮你 debug

**"不会 PyTorch"**  
→ 先用难度 1 的 numpy 版本，或者让 AI 给你一个 numpy 实现

**"没有运行环境"**  
→ 使用 Google Colab（免费，不需要安装任何东西）：colab.research.google.com

---

[← Day 17](day17.md) | [返回总览](../README.md) | [Day 19 →](day19.md)
