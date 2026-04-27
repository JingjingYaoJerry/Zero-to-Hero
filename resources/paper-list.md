# 📖 经典机器学习论文列表（50 篇）

> 按优先级排列。不需要全读，按方向和需求选择。  
> 📌 = 必读（建议所有 ML 工程师）  
> 🔤 = NLP/大模型方向推荐  
> 👁️ = CV 方向推荐  
> 📊 = 推荐/广告方向推荐  
> 🔧 = 传统 ML 工程推荐

---

## A. 基础必读（所有方向）

| 优先级 | 论文/概念 | 年份 | 核心贡献 | 搜索关键词 |
|-------|---------|------|---------|-----------|
| 📌 1 | **Adam: A Method for Stochastic Optimization** | 2015 | 动量 + 自适应学习率 | Adam optimizer Kingma Ba |
| 📌 2 | **Dropout** | 2014 | 正则化，防止过拟合 | Dropout Srivastava Hinton |
| 📌 3 | **Batch Normalization** | 2015 | 训练稳定性，加速收敛 | Batch Normalization Ioffe Szegedy |
| 📌 4 | **Deep Residual Learning (ResNet)** | 2016 | 残差连接，深层网络训练 | ResNet He Zhang |
| 📌 5 | **Attention Is All You Need (Transformer)** | 2017 | Self-Attention 架构 | Transformer Vaswani |
| 📌 6 | **Word2Vec** | 2013 | 分布式词表示 | Word2Vec Mikolov |
| 📌 7 | **Backpropagation** | 经典 | 梯度反向传播 | Backpropagation Rumelhart Hinton |
| 📌 8 | **XGBoost** | 2016 | 梯度提升树，工业界常用 | XGBoost Chen Guestrin |

---

## B. 深度学习架构

| 优先级 | 论文/概念 | 年份 | 核心贡献 | 搜索关键词 |
|-------|---------|------|---------|-----------|
| 📌 9 | **Bahdanau Attention** | 2015 | 注意力机制，Seq2Seq 改进 | Neural Machine Translation Bahdanau |
| 10 | **DenseNet** | 2017 | 密集连接，特征复用 | DenseNet Huang |
| 11 | **EfficientNet** | 2019 | 模型缩放，NAS | EfficientNet Tan Le |
| 12 | **LeNet / AlexNet / VGG** | 1998-2014 | CNN 基础架构演进 | AlexNet Krizhevsky |
| 13 | **Layer Normalization** | 2016 | Transformer 的 Norm | Layer Normalization Ba |

---

## C. NLP / 大模型方向

| 优先级 | 论文/概念 | 年份 | 核心贡献 | 搜索关键词 |
|-------|---------|------|---------|-----------|
| 🔤 14 | **BERT** | 2019 | 双向预训练，预训练+微调范式 | BERT Devlin |
| 🔤 15 | **GPT（系列）** | 2018+ | 自回归生成，规模化 | GPT OpenAI |
| 🔤 16 | **RoBERTa** | 2019 | BERT 训练优化 | RoBERTa Liu |
| 🔤 17 | **T5** | 2020 | Text-to-Text 统一框架 | T5 Raffel Google |
| 🔤 18 | **LoRA** | 2022 | 参数高效微调 | LoRA Low-Rank Adaptation Hu |
| 🔤 19 | **InstructGPT / RLHF** | 2022 | 人类反馈强化学习 | InstructGPT RLHF OpenAI |
| 🔤 20 | **DPO** | 2023 | 直接偏好优化 | Direct Preference Optimization Rafailov |
| 🔤 21 | **RAG** | 2020 | 检索增强生成 | Retrieval Augmented Generation Lewis |
| 🔤 22 | **Seq2Seq** | 2014 | 编码器-解码器架构 | Sequence to Sequence Sutskever |
| 🔤 23 | **Prefix Tuning / Prompt Tuning** | 2021 | 软提示微调 | Prefix Tuning Li Liang |

---

## D. 计算机视觉方向

| 优先级 | 论文/概念 | 年份 | 核心贡献 | 搜索关键词 |
|-------|---------|------|---------|-----------|
| 👁️ 24 | **Faster R-CNN** | 2015 | 两阶段目标检测，RPN | Faster R-CNN Ren |
| 👁️ 25 | **Mask R-CNN** | 2017 | 实例分割，RoIAlign | Mask R-CNN He |
| 👁️ 26 | **ViT（Vision Transformer）** | 2021 | Transformer 用于图像 | ViT Dosovitskiy |
| 👁️ 27 | **DETR** | 2020 | Transformer 做目标检测 | DETR Carion Facebook |
| 👁️ 28 | **CLIP** | 2021 | 图文对比学习 | CLIP Radford OpenAI |
| 👁️ 29 | **DDPM（Diffusion）** | 2020 | 扩散模型基础 | Denoising Diffusion Ho |
| 👁️ 30 | **Stable Diffusion（DDPM）** | 2022 | 潜在扩散模型 | Latent Diffusion Rombach |
| 👁️ 31 | **Swin Transformer** | 2021 | 分层 ViT，窗口注意力 | Swin Transformer Liu |
| 👁️ 32 | **U-Net** | 2015 | 医学图像分割，编码解码 | U-Net Ronneberger |

---

## E. 推荐 / 广告方向

| 优先级 | 论文/概念 | 年份 | 核心贡献 | 搜索关键词 |
|-------|---------|------|---------|-----------|
| 📊 33 | **Wide & Deep** | 2016 | 记忆 + 泛化，推荐基础 | Wide Deep Google |
| 📊 34 | **DeepFM** | 2017 | FM + DNN，特征交叉 | DeepFM Guo |
| 📊 35 | **DSSM（双塔模型）** | 2013 | 双塔召回，向量检索 | DSSM Huang Microsoft |
| 📊 36 | **DIN** | 2018 | 用户兴趣注意力机制 | DIN Zhou Alibaba |
| 📊 37 | **DIEN** | 2019 | 兴趣序列演化 | DIEN Zhou Alibaba |
| 📊 38 | **FM（Factorization Machine）** | 2010 | 特征交叉，推荐基础 | Factorization Machine Rendle |
| 📊 39 | **NCF** | 2017 | 神经协同过滤 | Neural Collaborative Filtering He |

---

## F. 传统机器学习

| 优先级 | 论文/概念 | 年份 | 核心贡献 | 搜索关键词 |
|-------|---------|------|---------|-----------|
| 🔧 40 | **SVM（支持向量机）** | 1995 | 最大间隔分类 | Support Vector Machine Vapnik |
| 🔧 41 | **Random Forest** | 2001 | Bagging + 随机特征 | Random Forest Breiman |
| 🔧 42 | **GBDT / Gradient Boosting** | 1999+ | 梯度提升树 | Gradient Boosting Friedman |
| 🔧 43 | **LightGBM** | 2017 | 高效 GBDT，直方图优化 | LightGBM Ke Microsoft |
| 🔧 44 | **PCA** | 经典 | 主成分分析，降维 | Principal Component Analysis |
| 🔧 45 | **Knowledge Distillation** | 2015 | 模型压缩，Teacher-Student | Knowledge Distillation Hinton |

---

## G. 训练技巧与其他

| 优先级 | 论文/概念 | 年份 | 核心贡献 | 搜索关键词 |
|-------|---------|------|---------|-----------|
| 46 | **Label Smoothing** | 2016 | 防止过度自信 | Label Smoothing Szegedy |
| 47 | **Mixup** | 2018 | 数据增强，线性插值 | Mixup Zhang |
| 48 | **Contrastive Learning（对比学习）** | 2020 | 自监督表示学习 | SimCLR Chen Google |
| 49 | **GAN（生成对抗网络）** | 2014 | 对抗生成，生成模型基础 | GAN Goodfellow |
| 50 | **LSTM** | 1997 | 长短时记忆网络 | LSTM Hochreiter Schmidhuber |

---

## 推荐阅读顺序

### 第 1 阶段（必读，约 2 周）

1. Backpropagation
2. Adam
3. Dropout
4. Batch Normalization
5. Word2Vec
6. ResNet
7. Bahdanau Attention
8. Transformer

### 第 2 阶段（按方向选，约 1-2 周）

**NLP 方向：** BERT → GPT → RoBERTa → LoRA → RAG  
**CV 方向：** Faster R-CNN → ViT → DETR → Diffusion 基础  
**推荐方向：** Wide&Deep → DeepFM → DSSM → DIN  
**传统 ML：** SVM → Random Forest → XGBoost → LightGBM  

### 第 3 阶段（扩展，按兴趣）

知识蒸馏、对比学习、其他方向经典论文

---

## 如何找到论文原文

1. **arXiv（免费）：** https://arxiv.org — 搜索论文标题
2. **Papers With Code：** https://paperswithcode.com — 有代码实现
3. **Semantic Scholar：** https://www.semanticscholar.org
4. **Google Scholar：** https://scholar.google.com

---

← [返回主页](../README.md)
