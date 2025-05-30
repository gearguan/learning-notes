---
layout: home
title: "学习笔记"
---

# 我的学习笔记

这里记录了我在机器人学、强化学习、深度学习等领域的学习过程中的知识点、思考和总结。网站支持：

## 功能特色

- 📝 **Markdown 写作**：使用简洁的 Markdown 语法
- 🔢 **数学公式**：支持 LaTeX 数学公式渲染
- 🖼️ **图片管理**：支持图片上传和引用
- 📊 **图表支持**：可插入各种图表和表格
- 🔗 **交叉引用**：支持图片、表格、公式的交叉引用
- 📱 **响应式设计**：在各种设备上都有良好的显示效果

## 最新笔记

{% for note in site.notes limit:5 %}
- [{{ note.title }}]({{ note.url | relative_url }}) - {{ note.date | date: "%Y-%m-%d" }}
{% endfor %}

## 开始使用

1. 查看 [示例笔记]({{ "/notes/example-note/" | relative_url }}) 了解如何使用各种功能
2. 浏览 [学习笔记]({{ "/notes/" | relative_url }}) 查看所有笔记
3. 了解更多 [关于本站]({{ "/about/" | relative_url }})

---

*最后更新：{{ site.time | date: "%Y年%m月%d日" }}* 