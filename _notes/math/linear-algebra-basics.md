---
# Jekyll布局模板，note是自定义的笔记布局，用于统一笔记页面的显示格式
layout: note

# 笔记标题，会显示在页面顶部和浏览器标签页中
# 建议使用清晰、描述性的标题
title: "线性代数基础"

# 创建日期，格式为YYYY-MM-DD，用于笔记排序和时间线显示
# Jekyll会使用此日期进行内容排序
date: 2024-01-20

# 分类标签，用于网站导航和内容组织
# 使用数组格式，可以包含多个分类
# 保持与现有网站结构一致，使用中文分类名
categories: [数学]

# 标签列表，用于内容搜索、相关文章推荐和主题聚合
# 建议使用具体的概念或关键词作为标签
# 有助于读者发现相关内容
tags: [线性代数, 矩阵, 向量空间]

# 学科分类，用于按学科浏览笔记和生成学科统计
# 可选值：数学、深度学习、机器人学、强化学习等
# 与categories配合使用，提供更精确的分类
subject: "数学"

# 难度等级，帮助读者选择合适的学习内容
# 建议使用统一的难度标准：入门、基础、初级、中级、高级、专家级
# 当前使用"基础"，建议统一为"初级"
difficulty: "基础"

# 参考文献列表，提供学习资源和引用来源
# 使用YAML列表格式，每个条目一行
# 包含教材、在线课程、论文等相关资源
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

矩阵乘法可以理解为线性变换的复合操作。

对于矩阵 $\mathbf{A} \in \mathbb{R}^{m \times n}$ 和 $\mathbf{B} \in \mathbb{R}^{n \times p}$，其乘积 $\mathbf{C} = \mathbf{AB}$ 的元素为：

$$\begin{equation}
c_{ij} = \sum_{k=1}^{n} a_{ik}b_{kj} \label{eq-matrix-mult}
\end{equation}$$

> **注释**：矩阵乘法不满足交换律，即一般情况下 $\mathbf{A}\mathbf{B} \neq \mathbf{B}\mathbf{A}$。

## 3. 重要性质总结

如[表1](#table-properties)所示的重要性质：

<div id="table-properties" class="table-wrapper">
<div class="table-caption">向量和矩阵的重要性质</div>

<table>
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

## 4. 应用实例

根据[公式 (1)](#eq-vector)和[公式 (4)](#eq-matrix-mult)，我们可以解决实际的线性变换问题。矩阵乘法可以理解为线性变换的复合，这在计算机图形学、机器学习等领域有广泛应用。

## 总结

本笔记介绍了线性代数的基础概念：
- 向量的定义和运算（[公式 (1)](#eq-vector)、[公式 (2)](#eq-vector-add)）
- 矩阵乘法的计算方法（[公式 (4)](#eq-matrix-mult)）
- 重要性质的对比（[表1](#table-properties)）

这些概念为后续学习特征值、特征向量等高级主题奠定了基础。 