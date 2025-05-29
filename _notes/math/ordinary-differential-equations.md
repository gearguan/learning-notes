---
layout: note
title: "常微分方程基础"
date: 2024-01-28
categories: [数学]
tags: [微分方程, 常微分方程, 解析解, 数值解]
subject: "数学"
difficulty: "中级"
references:
  - "Dennis G. Zill: A First Course in Differential Equations"
  - "William E. Boyce: Elementary Differential Equations"
---

# 常微分方程基础

常微分方程(ODE)是含有未知函数及其导数的方程，是数学分析和工程应用中的重要工具。

## 1. 基本概念

### 1.1 微分方程的定义

常微分方程的一般形式如[公式 (1)](#eq-general-ode)所示：

$$\begin{equation}
F(x, y, y', y'', \ldots, y^{(n)}) = 0 \label{eq-general-ode}
\end{equation}$$

其中 $y = y(x)$ 是未知函数，$y', y'', \ldots, y^{(n)}$ 是其各阶导数。

### 1.2 分类与特征

如[表1](#table-ode-classification)所示的常微分方程分类：

<div id="table-ode-classification" class="table-wrapper">
<div class="table-caption">常微分方程分类与特征</div>

<table>
<thead>
<tr>
  <th>分类方式</th>
  <th>类型</th>
  <th>特征</th>
  <th>求解难度</th>
</tr>
</thead>
<tbody>
<tr>
  <td><strong>按阶数</strong></td>
  <td>一阶</td>
  <td>只含一阶导数</td>
  <td>相对简单</td>
</tr>
<tr>
  <td></td>
  <td>高阶</td>
  <td>含二阶及以上导数</td>
  <td>复杂</td>
</tr>
<tr>
  <td><strong>按线性性</strong></td>
  <td>线性</td>
  <td>关于y及其导数线性</td>
  <td>有系统方法</td>
</tr>
<tr>
  <td></td>
  <td>非线性</td>
  <td>含y或导数的非线性项</td>
  <td>困难</td>
</tr>
<tr>
  <td><strong>按系数</strong></td>
  <td>常系数</td>
  <td>系数为常数</td>
  <td>较容易</td>
</tr>
<tr>
  <td></td>
  <td>变系数</td>
  <td>系数为变量函数</td>
  <td>复杂</td>
</tr>
</tbody>
</table>

</div>

## 2. 一阶微分方程

### 2.1 可分离变量方程

形如 $\frac{dy}{dx} = f(x)g(y)$ 的方程，通过分离变量求解：

$$\begin{equation}
\frac{dy}{g(y)} = f(x)dx \label{eq-separable}
\end{equation}$$

### 2.2 一阶线性方程

标准形式如[公式 (3)](#eq-first-order-linear)所示：

$$\begin{equation}
\frac{dy}{dx} + P(x)y = Q(x) \label{eq-first-order-linear}
\end{equation}$$

通解为：

$$\begin{equation}
y = e^{-\int P(x)dx}\left[\int Q(x)e^{\int P(x)dx}dx + C\right] \label{eq-first-order-solution}
\end{equation}$$

## 3. 二阶线性微分方程

### 3.1 齐次方程

二阶线性齐次方程的标准形式：

$$\begin{equation}
y'' + p(x)y' + q(x)y = 0 \label{eq-second-order-homogeneous}
\end{equation}$$

### 3.2 常系数齐次方程

对于常系数方程 $y'' + ay' + by = 0$，特征方程为：

$$\begin{equation}
r^2 + ar + b = 0 \label{eq-characteristic}
\end{equation}$$

如[表2](#table-characteristic-roots)所示的不同根的情况：

<div id="table-characteristic-roots" class="table-wrapper">
<div class="table-caption">特征根与通解形式</div>

<table>
<thead>
<tr>
  <th>特征根类型</th>
  <th>判别式</th>
  <th>根的形式</th>
  <th>通解形式</th>
</tr>
</thead>
<tbody>
<tr>
  <td><strong>两个不同实根</strong></td>
  <td>$\Delta > 0$</td>
  <td>$r_1, r_2$ (实数)</td>
  <td>$y = C_1e^{r_1x} + C_2e^{r_2x}$</td>
</tr>
<tr>
  <td><strong>重根</strong></td>
  <td>$\Delta = 0$</td>
  <td>$r_1 = r_2 = r$</td>
  <td>$y = (C_1 + C_2x)e^{rx}$</td>
</tr>
<tr>
  <td><strong>复数根</strong></td>
  <td>$\Delta < 0$</td>
  <td>$r = \alpha \pm i\beta$</td>
  <td>$y = e^{\alpha x}(C_1\cos\beta x + C_2\sin\beta x)$</td>
</tr>
</tbody>
</table>

</div>

## 4. 数值方法

### 4.1 欧拉方法

对于初值问题 $y' = f(x,y)$，$y(x_0) = y_0$，欧拉方法的迭代公式为：

$$\begin{equation}
y_{n+1} = y_n + h \cdot f(x_n, y_n) \label{eq-euler}
\end{equation}$$

### 4.2 龙格-库塔方法

四阶龙格-库塔方法具有更高的精度：

$$\begin{equation}
y_{n+1} = y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4) \label{eq-runge-kutta}
\end{equation}$$

其中：
- $k_1 = f(x_n, y_n)$
- $k_2 = f(x_n + \frac{h}{2}, y_n + \frac{h}{2}k_1)$
- $k_3 = f(x_n + \frac{h}{2}, y_n + \frac{h}{2}k_2)$
- $k_4 = f(x_n + h, y_n + hk_3)$

## 5. 应用实例

### 5.1 人口增长模型

简单的人口增长可以用一阶线性方程描述：

$$\begin{equation}
\frac{dP}{dt} = rP \label{eq-population}
\end{equation}$$

解得：$P(t) = P_0 e^{rt}$

### 5.2 弹簧振动

无阻尼弹簧振动满足二阶线性方程：

$$\begin{equation}
m\frac{d^2x}{dt^2} + kx = 0 \label{eq-spring}
\end{equation}$$

## 总结

本笔记介绍了常微分方程的基础知识：

- **基本概念**：微分方程的定义和分类（[公式 (1)](#eq-general-ode)、[表1](#table-ode-classification)）
- **一阶方程**：可分离变量和线性方程的求解（[公式 (2)](#eq-separable)、[公式 (3)](#eq-first-order-linear)）
- **二阶方程**：特征根方法和通解形式（[公式 (6)](#eq-characteristic)、[表2](#table-characteristic-roots)）
- **数值方法**：欧拉法和龙格-库塔法（[公式 (7)](#eq-euler)、[公式 (8)](#eq-runge-kutta)）

这些方法为解决物理、工程和生物等领域的动态系统问题提供了有力工具。 