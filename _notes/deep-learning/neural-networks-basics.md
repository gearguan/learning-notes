---
layout: note
title: "神经网络基础"
date: 2024-01-25
categories: [深度学习]
tags: [神经网络, 反向传播, 梯度下降]
subject: "深度学习"
difficulty: "中级"
references:
  - "Ian Goodfellow: Deep Learning"
  - "Michael Nielsen: Neural Networks and Deep Learning"
---

# 神经网络基础

神经网络是深度学习的基础，本笔记介绍神经网络的基本概念和训练方法。

## 1. 神经网络结构

### 1.1 感知机模型

单个神经元的数学模型如[公式 (1)](#eq-perceptron)所示：

$$\begin{equation}
y = f\left(\sum_{i=1}^{n} w_i x_i + b\right) = f(\mathbf{w}^T\mathbf{x} + b) \label{eq-perceptron}
\end{equation}$$

其中 $f$ 是激活函数，$\mathbf{w}$ 是权重向量，$b$ 是偏置。

### 1.2 多层神经网络

如[图1](#fig-neural-network)所示的典型三层神经网络结构：

<figure id="fig-neural-network">
<img src="/images/deep-learning/neural-network-structure.png" alt="神经网络结构图" style="width: 100%; max-width: 600px;">
<figcaption>三层神经网络结构示意图</figcaption>
</figure>

## 2. 激活函数

### 2.1 常用激活函数

如[表1](#table-activation)所示的常用激活函数对比：

<div id="table-activation" class="table-wrapper">
<div class="table-caption">常用激活函数对比</div>

| 激活函数 | 公式 | 范围 | 优点 | 缺点 |
|----------|------|------|------|------|
| Sigmoid | $\sigma(x) = \frac{1}{1+e^{-x}}$ | (0,1) | 平滑可导 | 梯度消失 |
| Tanh | $\tanh(x) = \frac{e^x-e^{-x}}{e^x+e^{-x}}$ | (-1,1) | 零中心 | 梯度消失 |
| ReLU | $\text{ReLU}(x) = \max(0,x)$ | [0,∞) | 计算简单 | 神经元死亡 |
| Leaky ReLU | $\text{LReLU}(x) = \max(\alpha x, x)$ | (-∞,∞) | 避免死亡 | 超参数选择 |

</div>

## 3. 反向传播算法

### 3.1 损失函数

对于回归问题，常用均方误差损失如[公式 (2)](#eq-mse)所示：

$$\begin{equation}
L = \frac{1}{2m}\sum_{i=1}^{m}(y_i - \hat{y}_i)^2 \label{eq-mse}
\end{equation}$$

### 3.2 梯度计算

根据链式法则，权重的梯度为：

$$\begin{equation}
\frac{\partial L}{\partial w_{ij}} = \frac{\partial L}{\partial y} \cdot \frac{\partial y}{\partial z} \cdot \frac{\partial z}{\partial w_{ij}} \label{eq-gradient}
\end{equation}$$

## 4. 训练过程

### 4.1 梯度下降

权重更新规则如[公式 (4)](#eq-weight-update)所示：

$$\begin{equation}
w_{new} = w_{old} - \eta \frac{\partial L}{\partial w} \label{eq-weight-update}
\end{equation}$$

其中 $\eta$ 是学习率。

## 总结

本笔记介绍了神经网络的基础概念：

- **网络结构**：从感知机到多层网络（[公式 (1)](#eq-perceptron)、[图1](#fig-neural-network)）
- **激活函数**：各种激活函数的特点（[表1](#table-activation)）
- **训练算法**：反向传播和梯度下降（[公式 (2)](#eq-mse)、[公式 (3)](#eq-gradient)、[公式 (4)](#eq-weight-update)）

这些概念是理解更复杂网络结构（CNN、RNN等）的基础。 