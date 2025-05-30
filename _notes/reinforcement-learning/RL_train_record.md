---
layout: note
title: "强化学习训练经验"
date: 2025-05-30
categories: [强化学习]
# tags: [agent, environment, episode length]
subject: "强化学习"
difficulty: "无"
# references:
#   - "John J. Craig: Introduction to Robotics"
#   - "Bruno Siciliano: Robotics: Modelling, Planning and Control"
---

# 框架对比

## Legged_gym

## Humanoid_gym

## IsaacEnvs(AMP)

## NP3O

# 超参数调节

- episode length: 可以适当缩短，但不要加长，试了从20秒加到30秒，短时间内 mean reward 飞速上升，但几百轮后策略无法收敛最终失败，尝试几十次无一例外。

## 总结

本笔记介绍了机器人运动学的基础概念：

- **坐标变换**：齐次变换矩阵（[公式 (1)](#eq-transform)）和DH参数（[表1](#table-dh-params)）
- **正运动学**：从关节角到末端位姿（[公式 (2)](#eq-forward-kinematics)、[公式 (3)](#eq-dh-transform)）
- **逆运动学**：从末端位姿到关节角（[公式 (4)](#eq-inverse-kinematics)、[表2](#table-solution-analysis)）
- **速度关系**：雅可比矩阵的应用（[公式 (5)](#eq-jacobian)）

这些概念是机器人控制和路径规划的基础。 