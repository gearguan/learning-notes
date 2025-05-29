---
layout: page
title: "关于"
permalink: /about/
---

# 关于本站

欢迎来到我的学习笔记网站！这里记录了我在学习过程中的思考、总结和收获。

## 网站特色

### 📝 专业的学术写作支持
- **数学公式**：支持 LaTeX 语法的数学公式渲染
- **交叉引用**：可以在文中引用图片、表格和公式
- **自动编号**：图表和公式自动编号，无需手动管理
- **响应式设计**：在各种设备上都有良好的显示效果

### 🔗 强大的引用功能
- 点击引用链接自动跳转到对应位置
- 目标元素高亮显示，便于定位
- 支持多种引用格式：图片、表格、公式

### 📊 多媒体内容支持
- 图片展示和管理
- 表格数据呈现
- 代码语法高亮
- 丰富的 Markdown 格式

## 技术架构

本网站基于以下技术构建：

- **Jekyll**：静态网站生成器
- **GitHub Pages**：免费托管服务
- **MathJax**：数学公式渲染
- **Minima**：简洁美观的主题
- **Markdown**：简单易用的写作语法

## 使用指南

### 如何写作
1. 在 `_notes` 目录下创建新的 Markdown 文件
2. 使用 YAML front matter 设置标题、日期、标签等信息
3. 使用 Markdown 语法编写内容
4. 添加图片到 `images` 目录
5. 使用交叉引用功能引用图表和公式

### 示例模板
```markdown
---
layout: note
title: "笔记标题"
date: 2024-01-15
tags: [标签1, 标签2]
references:
  - "参考资料1"
  - "参考资料2"
---

# 笔记内容

这里是笔记的正文内容...

如[图1](#fig-1)所示：

<figure id="fig-1">
<img src="/images/example.png" alt="示例图片">
<figcaption>图片说明</figcaption>
</figure>
```

## 联系方式

如果您对本站有任何建议或问题，欢迎通过以下方式联系我：

- **邮箱**：gearguan@gmail.com
- **GitHub**：[查看源代码](https://github.com/gearguan/study-notes-website)

## 版权声明

本站所有内容均为个人学习笔记，仅供参考。如有引用他人内容，会在参考资料中注明出处。

---

*最后更新：{{ site.time | date: "%Y年%m月%d日" }}* 