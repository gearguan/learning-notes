---
layout: page
title: "学科分类"
permalink: /subjects/
---

# 📚 学科分类

按学科领域组织的学习笔记，方便您根据兴趣和需求查找相关内容。

## 🔢 数学 (Mathematics)

数学是所有科学的基础，这里收录了各个数学分支的学习笔记。

### 📖 笔记列表
{% assign math_notes = site.notes | where_exp: "note", "note.categories contains '数学'" %}
{% for note in math_notes %}
- [{{ note.title }}]({{ note.url | relative_url }}) 
  - 📅 {{ note.date | date: "%Y-%m-%d" }}
  - 🏷️ {% for tag in note.tags %}{{ tag }}{% unless forloop.last %}, {% endunless %}{% endfor %}
  - 📊 难度：{{ note.difficulty }}
  - 🔗 URL调试：{{ note.url | relative_url }}
{% endfor %}

### 🎯 学习路径建议
1. **基础阶段**：线性代数、微积分
2. **进阶阶段**：概率论、数理统计
3. **高级阶段**：实分析、泛函分析

---

## 🤖 机器人学 (Robotics)

机器人学融合了机械、电子、计算机等多个学科，是现代工程的重要分支。

### 📖 笔记列表
{% assign robotics_notes = site.notes | where_exp: "note", "note.categories contains '机器人学'" %}
{% for note in robotics_notes %}
- [{{ note.title }}]({{ note.url | relative_url }})
  - 📅 {{ note.date | date: "%Y-%m-%d" }}
  - 🏷️ {% for tag in note.tags %}{{ tag }}{% unless forloop.last %}, {% endunless %}{% endfor %}
  - 📊 难度：{{ note.difficulty }}
  - 🔗 URL调试：{{ note.url | relative_url }}
{% endfor %}

### 🎯 学习路径建议
1. **基础阶段**：运动学、动力学
2. **进阶阶段**：控制理论、路径规划
3. **高级阶段**：多机器人系统、人机交互

---

## 🧠 深度学习 (Deep Learning)

深度学习是人工智能的核心技术，推动了计算机视觉、自然语言处理等领域的发展。

### 📖 笔记列表
{% assign dl_notes = site.notes | where_exp: "note", "note.categories contains '深度学习'" %}
{% for note in dl_notes %}
- [{{ note.title }}]({{ note.url | relative_url }})
  - 📅 {{ note.date | date: "%Y-%m-%d" }}
  - 🏷️ {% for tag in note.tags %}{{ tag }}{% unless forloop.last %}, {% endunless %}{% endfor %}
  - 📊 难度：{{ note.difficulty }}
  - 🔗 URL调试：{{ note.url | relative_url }}
{% endfor %}

### 🎯 学习路径建议
1. **基础阶段**：神经网络、反向传播
2. **进阶阶段**：CNN、RNN、Transformer
3. **高级阶段**：生成模型、强化学习结合

---

## 🎮 强化学习 (Reinforcement Learning)

强化学习通过与环境交互来学习最优策略，是实现人工智能的重要方法。

### 📖 笔记列表
{% assign rl_notes = site.notes | where_exp: "note", "note.categories contains '强化学习'" %}
{% for note in rl_notes %}
- [{{ note.title }}]({{ note.url | relative_url }})
  - 📅 {{ note.date | date: "%Y-%m-%d" }}
  - 🏷️ {% for tag in note.tags %}{{ tag }}{% unless forloop.last %}, {% endunless %}{% endfor %}
  - 📊 难度：{{ note.difficulty }}
  - 🔗 URL调试：{{ note.url | relative_url }}
{% endfor %}

### 🎯 学习路径建议
1. **基础阶段**：马尔可夫决策过程、动态规划
2. **进阶阶段**：Q-Learning、策略梯度
3. **高级阶段**：深度强化学习、多智能体系统

---

## 📊 统计信息

<div id="stats-table" class="table-wrapper">
<div class="table-caption">各学科笔记统计</div>

<table class="stats-table">
<thead>
<tr>
  <th>学科</th>
  <th>笔记数量</th>
  <th>最新更新</th>
  <th>平均难度</th>
</tr>
</thead>
<tbody>
<tr>
  <td><strong>🔢 数学</strong></td>
  <td>{{ math_notes | size }}</td>
  <td>{% if math_notes.size > 0 %}{{ math_notes | map: 'date' | sort | reverse | first | date: "%Y-%m-%d" }}{% else %}暂无{% endif %}</td>
  <td>基础-中级</td>
</tr>
<tr>
  <td><strong>🤖 机器人学</strong></td>
  <td>{{ robotics_notes | size }}</td>
  <td>{% if robotics_notes.size > 0 %}{{ robotics_notes | map: 'date' | sort | reverse | first | date: "%Y-%m-%d" }}{% else %}暂无{% endif %}</td>
  <td>中级-高级</td>
</tr>
<tr>
  <td><strong>🧠 深度学习</strong></td>
  <td>{{ dl_notes | size }}</td>
  <td>{% if dl_notes.size > 0 %}{{ dl_notes | map: 'date' | sort | reverse | first | date: "%Y-%m-%d" }}{% else %}暂无{% endif %}</td>
  <td>中级-高级</td>
</tr>
<tr>
  <td><strong>🎮 强化学习</strong></td>
  <td>{{ rl_notes | size }}</td>
  <td>{% if rl_notes.size > 0 %}{{ rl_notes | map: 'date' | sort | reverse | first | date: "%Y-%m-%d" }}{% else %}暂无{% endif %}</td>
  <td>高级</td>
</tr>
</tbody>
</table>

</div>

## 🔍 快速导航

- [📝 所有笔记](/notes/) - 查看所有笔记的时间线
- [🏷️ 标签索引](/tags/) - 按标签查找笔记
- [🔍 搜索](/search/) - 全文搜索功能
- [📈 学习进度](/progress/) - 追踪学习进度

---

## 💡 使用建议

1. **初学者**：建议从数学基础开始，为后续学习打下坚实基础
2. **有基础者**：可以根据兴趣选择特定领域深入学习
3. **跨学科学习**：这些领域相互关联，建议综合学习

<style>
.table-wrapper {
  margin: 20px 0;
  overflow-x: auto;
}

.table-caption {
  font-weight: bold;
  margin-bottom: 10px;
  color: #495057;
}

.stats-table {
  width: 100%;
  border-collapse: collapse;
  margin: 15px 0;
  font-size: 0.95em;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  border-radius: 8px;
  overflow: hidden;
}

.stats-table thead th {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  font-weight: bold;
  padding: 15px 12px;
  text-align: center;
  border: none;
}

.stats-table tbody td {
  padding: 12px 12px;
  border: 1px solid #e0e0e0;
  text-align: center;
  vertical-align: middle;
}

.stats-table tbody tr:nth-child(odd) {
  background-color: #f9f9f9;
}

.stats-table tbody tr:nth-child(even) {
  background-color: #ffffff;
}

.stats-table tbody tr:hover {
  background-color: #e8f4fd;
  transform: scale(1.01);
  transition: all 0.2s ease;
}

.stats-table tbody td:first-child {
  text-align: left;
  font-weight: bold;
  background-color: rgba(102, 126, 234, 0.1);
}

@media (max-width: 768px) {
  .stats-table {
    font-size: 0.85em;
  }
  
  .stats-table th,
  .stats-table td {
    padding: 8px 6px;
  }
}

hr {
  margin: 40px 0;
  border: none;
  border-top: 2px solid #e9ecef;
}

h2 {
  color: #2c3e50;
  border-bottom: 2px solid #3498db;
  padding-bottom: 10px;
}

.emoji {
  font-size: 1.2em;
}
</style> 