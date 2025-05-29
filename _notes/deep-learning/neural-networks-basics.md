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

<table class="activation-table">
<thead>
<tr>
  <th>激活函数</th>
  <th>函数表达式</th>
  <th>输出范围</th>
  <th>主要优点</th>
  <th>主要缺点</th>
</tr>
</thead>
<tbody>
<tr>
  <td><strong>Sigmoid</strong></td>
  <td>$\sigma(x) = \frac{1}{1+e^{-x}}$</td>
  <td>(0, 1)</td>
  <td>平滑可导</td>
  <td>梯度消失</td>
</tr>
<tr>
  <td><strong>Tanh</strong></td>
  <td>$\tanh(x) = \frac{e^x-e^{-x}}{e^x+e^{-x}}$</td>
  <td>(-1, 1)</td>
  <td>零中心化</td>
  <td>梯度消失</td>
</tr>
<tr>
  <td><strong>ReLU</strong></td>
  <td>$\max(0, x)$</td>
  <td>[0, ∞)</td>
  <td>计算简单</td>
  <td>神经元死亡</td>
</tr>
<tr>
  <td><strong>Leaky ReLU</strong></td>
  <td>$\max(\alpha x, x)$</td>
  <td>(-∞, ∞)</td>
  <td>避免死亡</td>
  <td>需调参数</td>
</tr>
</tbody>
</table>

</div>

<style>
.note-content .activation-table {
  width: 100%;
  border-collapse: collapse;
  margin: 15px 0;
  font-size: 0.9em;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.note-content .activation-table thead th {
  background-color: #2c3e50 !important;
  color: white !important;
  font-weight: bold;
  padding: 12px 8px;
  text-align: center;
  border: 1px solid #34495e;
}

.note-content .activation-table tbody td {
  padding: 10px 8px;
  border: 1px solid #bdc3c7;
  text-align: center;
  vertical-align: middle;
  background-color: white;
}

.note-content .activation-table tbody tr:nth-child(even) td {
  background-color: #f8f9fa !important;
}

.note-content .activation-table tbody tr:hover td {
  background-color: #e3f2fd !important;
}

.note-content .activation-table tbody td:first-child {
  font-weight: bold;
  background-color: #ecf0f1 !important;
  text-align: left;
}

@media (max-width: 768px) {
  .note-content .activation-table {
    font-size: 0.8em;
  }
  
  .note-content .activation-table th,
  .note-content .activation-table td {
    padding: 6px 4px;
  }
}
</style>

### 2.2 激活函数详细说明

**Sigmoid函数**：
- 公式：$\sigma(x) = \frac{1}{1+e^{-x}}$
- 特点：输出在0到1之间，常用于二分类
- 问题：深层网络中容易出现梯度消失

**Tanh函数**：
- 公式：$\tanh(x) = \frac{e^x-e^{-x}}{e^x+e^{-x}}$
- 特点：输出以0为中心，收敛速度比Sigmoid快
- 问题：同样存在梯度消失问题

**ReLU函数**：
- 公式：$\text{ReLU}(x) = \max(0, x)$
- 特点：计算简单，有效缓解梯度消失
- 问题：负值区域梯度为0，可能导致神经元死亡

**Leaky ReLU函数**：
- 公式：$\text{LeakyReLU}(x) = \max(\alpha x, x)$，其中$\alpha$是小正数（如0.01）
- 特点：在负值区域保持小的梯度，避免神经元死亡
- 问题：需要调整超参数$\alpha$

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