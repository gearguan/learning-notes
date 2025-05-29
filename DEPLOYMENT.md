# 部署指南：将学习笔记网站部署到 GitHub Pages

本指南将手把手教您如何将这个学习笔记网站部署到 GitHub Pages。

## 前提条件

1. 拥有 GitHub 账号（您的邮箱：gearguan@gmail.com）
2. 安装了 Git
3. 基本的命令行操作知识

## 步骤一：创建 GitHub 仓库

### 1.1 登录 GitHub
访问 [GitHub](https://github.com) 并登录您的账号。

### 1.2 创建新仓库
1. 点击右上角的 "+" 按钮，选择 "New repository"
2. 仓库名称建议使用：`study-notes-website` 或 `learning-notes`
3. 设置为 Public（公开）
4. 不要勾选 "Initialize this repository with a README"
5. 点击 "Create repository"

## 步骤二：上传代码到 GitHub

### 2.1 初始化 Git 仓库
在您的项目目录中打开命令行，执行：

```bash
git init
git add .
git commit -m "Initial commit: 学习笔记网站"
```

### 2.2 连接到 GitHub 仓库
将 `YOUR_USERNAME` 替换为您的 GitHub 用户名：

```bash
git remote add origin https://github.com/YOUR_USERNAME/study-notes-website.git
git branch -M main
git push -u origin main
```

## 步骤三：启用 GitHub Pages

### 3.1 进入仓库设置
1. 在 GitHub 上进入您的仓库页面
2. 点击 "Settings" 选项卡

### 3.2 配置 GitHub Pages
1. 在左侧菜单中找到 "Pages"
2. 在 "Source" 部分选择 "Deploy from a branch"
3. 选择 "main" 分支
4. 文件夹选择 "/ (root)"
5. 点击 "Save"

### 3.3 等待部署
- GitHub 会自动开始构建您的网站
- 通常需要几分钟时间
- 完成后会显示网站地址：`https://YOUR_USERNAME.github.io/study-notes-website`

## 步骤四：配置网站设置

### 4.1 更新 _config.yml
编辑 `_config.yml` 文件，更新以下内容：

```yaml
# 将 YOUR_USERNAME 替换为您的 GitHub 用户名
baseurl: "/study-notes-website"  # 如果仓库名不同，请相应修改
url: "https://YOUR_USERNAME.github.io"
```

### 4.2 提交更改
```bash
git add _config.yml
git commit -m "更新网站配置"
git push
```

## 步骤五：验证部署

### 5.1 检查网站
1. 等待几分钟让 GitHub Pages 重新构建
2. 访问您的网站：`https://YOUR_USERNAME.github.io/study-notes-website`
3. 确认所有页面都能正常访问

### 5.2 测试功能
- 检查首页是否正常显示
- 访问示例笔记页面
- 测试交叉引用功能（点击链接是否跳转）
- 验证数学公式是否正确渲染

## 步骤六：添加自定义域名（可选）

如果您有自己的域名，可以配置自定义域名：

### 6.1 添加 CNAME 文件
在项目根目录创建 `CNAME` 文件，内容为您的域名：
```
yourdomain.com
```

### 6.2 配置 DNS
在您的域名提供商处添加 CNAME 记录：
```
CNAME  www  YOUR_USERNAME.github.io
```

## 日常使用流程

### 添加新笔记
1. 在 `_notes` 目录创建新的 `.md` 文件
2. 使用提供的模板编写内容
3. 提交并推送到 GitHub：
   ```bash
   git add .
   git commit -m "添加新笔记：笔记标题"
   git push
   ```
4. 等待几分钟，新笔记会自动发布到网站

### 添加图片
1. 将图片放入 `images` 目录
2. 在笔记中使用相对路径引用
3. 提交并推送更改

## 故障排除

### 常见问题

**问题1：网站显示 404 错误**
- 检查 `_config.yml` 中的 `baseurl` 设置
- 确认仓库名称与配置一致

**问题2：数学公式不显示**
- 检查网络连接（MathJax 需要从 CDN 加载）
- 确认公式语法正确

**问题3：图片不显示**
- 检查图片路径是否正确
- 确认图片文件已上传到 GitHub

**问题4：样式显示异常**
- 清除浏览器缓存
- 检查 CSS 文件是否正确加载

### 调试方法

1. **查看构建日志**：
   - 在 GitHub 仓库的 "Actions" 选项卡查看构建状态
   - 如有错误，会显示详细的错误信息

2. **本地测试**：
   ```bash
   # 安装 Jekyll（需要 Ruby 环境）
   gem install bundler jekyll
   bundle install
   
   # 本地运行
   bundle exec jekyll serve
   
   # 访问 http://localhost:4000 测试
   ```

## 进阶配置

### 启用评论功能
可以集成 Disqus 或 Gitalk 评论系统。

### 添加搜索功能
可以使用 Jekyll 插件添加站内搜索。

### 自定义主题
可以修改 CSS 样式或使用其他 Jekyll 主题。

### 添加统计分析
可以集成 Google Analytics 进行访问统计。

## 支持

如果在部署过程中遇到问题，可以：

1. 查看 [Jekyll 官方文档](https://jekyllrb.com/docs/)
2. 查看 [GitHub Pages 文档](https://docs.github.com/en/pages)
3. 在项目仓库提交 Issue
4. 发送邮件到：gearguan@gmail.com

---

祝您部署顺利！🎉 