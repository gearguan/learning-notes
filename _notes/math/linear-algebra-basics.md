---
layout: note
title: "线性代数基础"
date: 2024-01-20
categories: [数学]
tags: [线性代数, 矩阵, 向量空间]
subject: "数学"
difficulty: "基础"
references:
  - "Gilbert Strang: Introduction to Linear Algebra"
  - "3Blue1Brown: Essence of Linear Algebra"
---

# 线性代数基础

本笔记介绍线性代数的基本概念，包括向量、矩阵运算和向量空间的基础知识。

## 1. 向量的基本概念

### 1.1 向量定义

向量是具有大小和方向的量。在 $n$ 维空间中，向量可以表示为：

$$\begin{equation}
\mathbf{v} = \begin{pmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{pmatrix} \label{eq-vector}
\end{equation}$$

### 1.2 向量运算

#### 向量加法
如[公式 (2)](#eq-vector-add)所示：

$$\begin{equation}
\mathbf{u} + \mathbf{v} = \begin{pmatrix} u_1 + v_1 \\ u_2 + v_2 \\ \vdots \\ u_n + v_n \end{pmatrix} \label{eq-vector-add}
\end{equation}$$

#### 数量乘法
$$\begin{equation}
c\mathbf{v} = \begin{pmatrix} cv_1 \\ cv_2 \\ \vdots \\ cv_n \end{pmatrix} \label{eq-scalar-mult}
\end{equation}$$

## 2. 矩阵运算

### 2.1 矩阵乘法

如[图1](#fig-matrix-mult)所示的矩阵乘法过程：

<figure id="fig-matrix-mult">
<img src="/images/math/matrix-multiplication.png" alt="矩阵乘法示意图" style="width: 100%; max-width: 600px;">
<figcaption>矩阵乘法的几何解释</figcaption>
</figure>

对于矩阵 $\mathbf{A} \in \mathbb{R}^{m \times n}$ 和 $\mathbf{B} \in \mathbb{R}^{n \times p}$，其乘积 $\mathbf{C} = \mathbf{AB}$ 的元素为：

$$\begin{equation}
c_{ij} = \sum_{k=1}^{n} a_{ik}b_{kj} \label{eq-matrix-mult}
\end{equation}$$

## 3. 重要性质总结

如[表1](#table-properties)所示的重要性质：

<div id="table-properties" class="table-wrapper">
<div class="table-caption">向量和矩阵的重要性质</div>

<table class="math-properties-table">
<thead>
<tr>
  <th>运算类型</th>
  <th>交换律</th>
  <th>结合律</th>
  <th>分配律</th>
</tr>
</thead>
<tbody>
<tr>
  <td><strong>向量加法</strong></td>
  <td>✓</td>
  <td>✓</td>
  <td>✓</td>
</tr>
<tr>
  <td><strong>矩阵加法</strong></td>
  <td>✓</td>
  <td>✓</td>
  <td>✓</td>
</tr>
<tr>
  <td><strong>矩阵乘法</strong></td>
  <td>✗</td>
  <td>✓</td>
  <td>✓</td>
</tr>
<tr>
  <td><strong>数量乘法</strong></td>
  <td>✓</td>
  <td>✓</td>
  <td>✓</td>
</tr>
</tbody>
</table>

</div>

<style>
.math-properties-table {
  width: 100%;
  border-collapse: collapse;
  margin: 15px 0;
  font-size: 0.9em;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.math-properties-table thead th {
  background-color: #2c3e50;
  color: white;
  font-weight: bold;
  padding: 12px 8px;
  text-align: center;
  border: 1px solid #34495e;
}

.math-properties-table tbody td {
  padding: 10px 8px;
  border: 1px solid #bdc3c7;
  text-align: center;
  vertical-align: middle;
}

.math-properties-table tbody tr:nth-child(even) {
  background-color: #f8f9fa;
}

.math-properties-table tbody tr:hover {
  background-color: #e3f2fd;
}

.math-properties-table tbody td:first-child {
  font-weight: bold;
  background-color: #ecf0f1;
  text-align: left;
}

@media (max-width: 768px) {
  .math-properties-table {
    font-size: 0.8em;
  }
  
  .math-properties-table th,
  .math-properties-table td {
    padding: 6px 4px;
  }
}
</style>

## 4. 应用实例

根据[公式 (1)](#eq-vector)和[公式 (4)](#eq-matrix-mult)，我们可以解决实际的线性变换问题。如[图1](#fig-matrix-mult)所示，矩阵乘法可以理解为线性变换的复合。

## 总结

本笔记介绍了线性代数的基础概念：
- 向量的定义和运算（[公式 (1)](#eq-vector)、[公式 (2)](#eq-vector-add)）
- 矩阵乘法的计算方法（[公式 (4)](#eq-matrix-mult)）
- 重要性质的对比（[表1](#table-properties)）

这些概念为后续学习特征值、特征向量等高级主题奠定了基础。 