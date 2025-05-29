# 学习笔记网站

这是一个基于 Jekyll 和 GitHub Pages 的学习笔记网站，支持数学公式、图片引用、表格和交叉引用功能。

## 功能特色

- 📝 **Markdown 写作**：使用简洁的 Markdown 语法
- 🔢 **数学公式**：支持 LaTeX 数学公式渲染（MathJax）
- 🖼️ **图片管理**：支持图片上传和引用
- 📊 **图表支持**：可插入各种图表和表格
- 🔗 **交叉引用**：支持图片、表格、公式的交叉引用
- 📱 **响应式设计**：在各种设备上都有良好的显示效果
- 🏷️ **标签分类**：按标签组织和查找笔记
- 🔍 **自动编号**：图表和公式自动编号

## 快速开始

### 1. 克隆仓库

```bash
git clone https://github.com/gearguan/study-notes-website.git
cd study-notes-website
```

### 2. 安装依赖

确保您已安装 Ruby 和 Bundler，然后运行：

```bash
bundle install
```

### 3. 本地运行

```bash
bundle exec jekyll serve
```

网站将在 `http://localhost:4000` 运行。

### 4. 部署到 GitHub Pages

1. 将代码推送到 GitHub 仓库
2. 在仓库设置中启用 GitHub Pages
3. 选择 `main` 分支作为源
4. 网站将自动部署到 `https://username.github.io/repository-name`

## 目录结构

```
study-notes-website/
├── _config.yml          # Jekyll 配置文件
├── _layouts/            # 页面布局模板
│   └── note.html       # 笔记页面布局
├── _notes/             # 学习笔记目录
│   └── example-note.md # 示例笔记
├── images/             # 图片资源目录
├── index.md            # 首页
├── notes.md            # 笔记列表页
├── about.md            # 关于页面
├── Gemfile             # Ruby 依赖管理
└── README.md           # 项目说明
```

## 使用指南

### 创建新笔记

1. 在 `_notes` 目录下创建新的 Markdown 文件
2. 使用以下模板：

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
```

### 添加图片

1. 将图片放在 `images` 目录中
2. 在笔记中使用以下格式引用：

```html
<figure id="fig-1">
<img src="/images/example.png" alt="示例图片">
<figcaption>图片说明</figcaption>
</figure>
```

3. 在文中引用：`如[图1](#fig-1)所示`

### 添加表格

```html
<div id="table-1" class="table-wrapper">
<div class="table-caption">表格标题</div>

| 列1 | 列2 | 列3 |
|-----|-----|-----|
| 数据1 | 数据2 | 数据3 |

</div>
```

在文中引用：`如[表1](#table-1)所示`

### 添加数学公式

行内公式：`$E = mc^2$`

独立公式：
```latex
$$\begin{equation}
E = mc^2 \label{eq-1}
\end{equation}$$
```

在文中引用：`如[公式 (1)](#eq-1)所示`

## 自定义配置

### 修改网站信息

编辑 `_config.yml` 文件：

```yaml
title: "您的网站标题"
description: "网站描述"
author: "您的姓名"
email: "您的邮箱"
url: "https://yourusername.github.io"
```

### 修改主题样式

可以通过修改 `_layouts/note.html` 中的 CSS 样式来自定义外观。

## 技术栈

- **Jekyll**：静态网站生成器
- **GitHub Pages**：免费托管服务
- **MathJax**：数学公式渲染
- **Minima**：Jekyll 主题
- **Kramdown**：Markdown 处理器

## 贡献

欢迎提交 Issue 和 Pull Request 来改进这个项目。

## 许可证

MIT License

## 联系方式

- 邮箱：gearguan@gmail.com
- GitHub：[@gearguan](https://github.com/gearguan)

---

*Happy Learning! 📚* 