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

<table class="dh-params-table">
<thead>
<tr>
  <th>参数名称</th>
  <th>数学符号</th>
  <th>物理含义</th>
  <th>取值范围</th>
</tr>
</thead>
<tbody>
<tr>
  <td><strong>连杆长度</strong></td>
  <td>$a_i$</td>
  <td>沿 $x_i$ 轴的距离</td>
  <td>$[0, +\infty)$</td>
</tr>
<tr>
  <td><strong>连杆扭转角</strong></td>
  <td>$\alpha_i$</td>
  <td>绕 $x_i$ 轴的角度</td>
  <td>$[-\pi, \pi]$</td>
</tr>
<tr>
  <td><strong>关节距离</strong></td>
  <td>$d_i$</td>
  <td>沿 $z_{i-1}$ 轴的距离</td>
  <td>$(-\infty, +\infty)$</td>
</tr>
<tr>
  <td><strong>关节角</strong></td>
  <td>$\theta_i$</td>
  <td>绕 $z_{i-1}$ 轴的角度</td>
  <td>$[-\pi, \pi]$</td>
</tr>
</tbody>
</table>

</div>

<style>
.note-content .dh-params-table {
  width: 100%;
  border-collapse: collapse;
  margin: 15px 0;
  font-size: 0.9em;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.note-content .dh-params-table thead th {
  background-color: #f5f5f5 !important;
  color: #333 !important;
  font-weight: bold;
  padding: 12px 8px;
  text-align: center;
  border: 1px solid #ddd;
}

.note-content .dh-params-table tbody td {
  padding: 10px 8px;
  border: 1px solid #bdc3c7;
  text-align: center;
  vertical-align: middle;
  background-color: white;
}

.note-content .dh-params-table tbody tr:nth-child(even) td {
  background-color: #f8f9fa !important;
}

.note-content .dh-params-table tbody tr:hover td {
  background-color: #e3f2fd !important;
}

.note-content .dh-params-table tbody td:first-child {
  font-weight: bold;
  background-color: #ecf0f1 !important;
  text-align: left;
}

@media (max-width: 768px) {
  .note-content .dh-params-table {
    font-size: 0.8em;
  }
  
  .note-content .dh-params-table th,
  .note-content .dh-params-table td {
    padding: 6px 4px;
  }
}
</style>

## 2. 正运动学

### 2.1 正运动学方程

如[图1](#fig-forward-kinematics)所示的正运动学过程：

<figure id="fig-forward-kinematics">
<img src="{{ '/images/robotics/forward-kinematics.jpg' | relative_url }}" alt="正运动学示意图" style="width: 100%; max-width: 700px;">
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

<table class="solution-analysis-table">
<thead>
<tr>
  <th>驱动情况</th>
  <th>自由度条件</th>
  <th>解的数量</th>
  <th>推荐求解方法</th>
</tr>
</thead>
<tbody>
<tr>
  <td><strong>欠驱动</strong></td>
  <td>DOF &lt; 6</td>
  <td>无解或无穷解</td>
  <td>伪逆法</td>
</tr>
<tr>
  <td><strong>恰好驱动</strong></td>
  <td>DOF = 6</td>
  <td>有限解</td>
  <td>解析法/数值法</td>
</tr>
<tr>
  <td><strong>冗余驱动</strong></td>
  <td>DOF &gt; 6</td>
  <td>无穷解</td>
  <td>优化方法</td>
</tr>
</tbody>
</table>

</div>

<style>
.note-content .solution-analysis-table {
  width: 100%;
  border-collapse: collapse;
  margin: 15px 0;
  font-size: 0.9em;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.note-content .solution-analysis-table thead th {
  background-color: #f5f5f5 !important;
  color: #333 !important;
  font-weight: bold;
  padding: 12px 8px;
  text-align: center;
  border: 1px solid #ddd;
}

.note-content .solution-analysis-table tbody td {
  padding: 10px 8px;
  border: 1px solid #bdc3c7;
  text-align: center;
  vertical-align: middle;
  background-color: white;
}

.note-content .solution-analysis-table tbody tr:nth-child(even) td {
  background-color: #f8f9fa !important;
}

.note-content .solution-analysis-table tbody tr:hover td {
  background-color: #e3f2fd !important;
}

.note-content .solution-analysis-table tbody td:first-child {
  font-weight: bold;
  background-color: #ecf0f1 !important;
  text-align: left;
}

@media (max-width: 768px) {
  .note-content .solution-analysis-table {
    font-size: 0.8em;
  }
  
  .note-content .solution-analysis-table th,
  .note-content .solution-analysis-table td {
    padding: 6px 4px;
  }
}
</style>

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