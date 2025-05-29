---
layout: note
title: "机器人运动学基础"
date: 2024-01-22
categories: [机器人学]
tags: [运动学, 正运动学, 逆运动学, DH参数]
subject: "机器人学"
difficulty: "中级"
references:
  - "John J. Craig: Introduction to Robotics"
  - "Bruno Siciliano: Robotics: Modelling, Planning and Control"
---

# 机器人运动学基础

机器人运动学研究机器人各关节位置与末端执行器位置之间的几何关系，是机器人学的基础。

## 1. 坐标系变换

### 1.1 齐次变换矩阵

机器人各关节之间的位置关系可以用齐次变换矩阵表示，如[公式 (1)](#eq-transform)所示：

$$\begin{equation}
{}^{i-1}T_i = \begin{pmatrix}
{}^{i-1}R_i & {}^{i-1}p_i \\
0 & 1
\end{pmatrix} \label{eq-transform}
\end{equation}$$

其中 ${}^{i-1}R_i$ 是旋转矩阵，${}^{i-1}p_i$ 是位置向量。

### 1.2 DH参数表示法

如[表1](#table-dh-params)所示的标准DH参数：

<div id="table-dh-params" class="table-wrapper">
<div class="table-caption">DH参数定义</div>

| 参数 | 符号 | 含义 | 取值范围 |
|------|------|------|----------|
| 连杆长度 | $a_i$ | 沿 $x_i$ 轴的距离 | $[0, +\infty)$ |
| 连杆扭转角 | $\alpha_i$ | 绕 $x_i$ 轴的角度 | $[-\pi, \pi]$ |
| 关节距离 | $d_i$ | 沿 $z_{i-1}$ 轴的距离 | $(-\infty, +\infty)$ |
| 关节角 | $\theta_i$ | 绕 $z_{i-1}$ 轴的角度 | $[-\pi, \pi]$ |

</div>

## 2. 正运动学

### 2.1 正运动学方程

如[图1](#fig-forward-kinematics)所示的正运动学过程：

<figure id="fig-forward-kinematics">
<img src="/images/robotics/forward-kinematics.png" alt="正运动学示意图" style="width: 100%; max-width: 700px;">
<figcaption>6自由度机器人正运动学示意图</figcaption>
</figure>

正运动学的变换矩阵为：

$$\begin{equation}
{}^0T_n = \prod_{i=1}^{n} {}^{i-1}T_i = {}^0T_1 \cdot {}^1T_2 \cdots {}^{n-1}T_n \label{eq-forward-kinematics}
\end{equation}$$

### 2.2 标准DH变换矩阵

根据[表1](#table-dh-params)的DH参数，标准变换矩阵为：

$$\begin{equation}
{}^{i-1}T_i = \begin{pmatrix}
\cos\theta_i & -\sin\theta_i\cos\alpha_i & \sin\theta_i\sin\alpha_i & a_i\cos\theta_i \\
\sin\theta_i & \cos\theta_i\cos\alpha_i & -\cos\theta_i\sin\alpha_i & a_i\sin\theta_i \\
0 & \sin\alpha_i & \cos\alpha_i & d_i \\
0 & 0 & 0 & 1
\end{pmatrix} \label{eq-dh-transform}
\end{equation}$$

## 3. 逆运动学

### 3.1 逆运动学问题

逆运动学求解给定末端执行器位姿时的关节角度。这是一个非线性方程组求解问题：

$$\begin{equation}
f(\mathbf{q}) = \mathbf{x}_d \label{eq-inverse-kinematics}
\end{equation}$$

其中 $\mathbf{q} = [\theta_1, \theta_2, ..., \theta_n]^T$ 是关节角向量，$\mathbf{x}_d$ 是期望的末端位姿。

### 3.2 解的存在性与唯一性

如[表2](#table-solution-analysis)所示的解的分析：

<div id="table-solution-analysis" class="table-wrapper">
<div class="table-caption">逆运动学解的特性分析</div>

| 情况 | 条件 | 解的数量 | 求解方法 |
|------|------|----------|----------|
| 欠驱动 | DOF < 6 | 无解或无穷解 | 伪逆法 |
| 恰好驱动 | DOF = 6 | 有限解 | 解析法/数值法 |
| 冗余驱动 | DOF > 6 | 无穷解 | 优化方法 |

</div>

## 4. 应用实例

### 4.1 PUMA 560机器人

参考[图1](#fig-forward-kinematics)和[公式 (3)](#eq-dh-transform)，PUMA 560机器人的正运动学可以通过连续的DH变换得到。

根据[表1](#table-dh-params)的参数定义和[公式 (2)](#eq-forward-kinematics)，我们可以计算末端执行器的位置。

## 5. 雅可比矩阵

### 5.1 速度雅可比

关节速度与末端速度的关系如[公式 (5)](#eq-jacobian)所示：

$$\begin{equation}
\mathbf{v} = J(\mathbf{q})\dot{\mathbf{q}} \label{eq-jacobian}
\end{equation}$$

其中 $J(\mathbf{q})$ 是雅可比矩阵，$\mathbf{v}$ 是末端速度，$\dot{\mathbf{q}}$ 是关节速度。

## 总结

本笔记介绍了机器人运动学的基础概念：

- **坐标变换**：齐次变换矩阵（[公式 (1)](#eq-transform)）和DH参数（[表1](#table-dh-params)）
- **正运动学**：从关节角到末端位姿（[公式 (2)](#eq-forward-kinematics)、[公式 (3)](#eq-dh-transform)）
- **逆运动学**：从末端位姿到关节角（[公式 (4)](#eq-inverse-kinematics)、[表2](#table-solution-analysis)）
- **速度关系**：雅可比矩阵的应用（[公式 (5)](#eq-jacobian)）

这些概念是机器人控制和路径规划的基础。 