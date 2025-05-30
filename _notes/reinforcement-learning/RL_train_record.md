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

### Legged_gym

项目地址：[Legged Gym](https://github.com/leggedrobotics/legged_gym/tree/master)

ETH苏黎世机器人系统实验室开发的基于Isaac Gym的足式机器人环境。该框架专门用于训练四足机器人在复杂地形上行走，包含了完整的sim-to-real迁移组件。

主要特点：
- 基于NVIDIA Isaac Gym物理仿真
- 支持ANYmal等多种足式机器人
- 包含地形随机化、摩擦随机化、质量随机化
- 提供噪声观测和训练期间随机推力
- 完整的PPO强化学习训练流程

### Humanoid_gym

项目地址：[Humanoid Gym](https://github.com/roboterax/humanoid-gym)

基于NVIDIA Isaac Gym的人形机器人强化学习框架，专注于零样本sim-to-real转移。该框架由RobotEra团队开发，已在XBot-S和XBot-L人形机器人上验证。

主要特点：
- 专门为人形机器人设计的奖励函数
- 零样本仿真到现实转移能力
- 集成sim-to-sim框架（Isaac Gym到Mujoco）
- 支持多帧低级控制
- 经过真实机器人验证的政策

### IsaacEnvs(AMP)

项目地址：[Isaac Gym Envs](https://github.com/isaac-sim/IsaacGymEnvs/tree/main)

NVIDIA官方的Isaac Gym环境集合，包含多种机器人学习任务。其中AMP（Adversarial Motion Priors）是重要组成部分，用于学习自然的运动模式。

主要特点：
- NVIDIA官方维护的标准环境
- 包含AMP对抗性运动先验
- 支持多种机器人类型
- 高性能GPU并行仿真
- 丰富的预训练模型和示例

### NP3O

项目地址：[Locomotion with NP3O](https://github.com/zeonsunlightyu/LocomotionWithNP3O)

基于Natural Policy Gradients with Proximal Policy Optimization的运动控制框架，专注于自然运动学习。

主要特点：
- 结合自然策略梯度和PPO 
- 专注于自然运动模式学习
- 改进的策略优化算法
- 适用于复杂运动控制任务

# 超参数调节

- episode length: 可以适当缩短，但不要加长，试了从20秒加到30秒，短时间内 mean reward 飞速上升，但几百轮后策略无法收敛最终失败，尝试几十次无一例外。

-  L2 损失（L2 loss）:也叫均方误差(Mean Squared Error, MSE)，比如当前高度与目标高度的平方差 $(h_current - h_target)^2$。除此之外，还有 L1、Huber、Cross Entropy 等多种损失函数，适用于不同任务和数据特性。选择合适的损失函数对模型性能至关重要。

## 总结

本笔记介绍了机器人运动学的基础概念：

- **坐标变换**：齐次变换矩阵（[公式 (1)](#eq-transform)）和DH参数（[表1](#table-dh-params)）
- **正运动学**：从关节角到末端位姿（[公式 (2)](#eq-forward-kinematics)、[公式 (3)](#eq-dh-transform)）
- **逆运动学**：从末端位姿到关节角（[公式 (4)](#eq-inverse-kinematics)、[表2](#table-solution-analysis)）
- **速度关系**：雅可比矩阵的应用（[公式 (5)](#eq-jacobian)）

这些概念是机器人控制和路径规划的基础。 