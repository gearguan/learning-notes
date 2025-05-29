# 快速修复指南

## 问题原因
您的网站样式问题和404链接错误是因为 `_config.yml` 中的 `baseurl` 配置不正确导致的。

## 解决步骤

请在 **Git Bash** 中执行以下命令：

```bash
# 1. 添加修改的文件
git add _config.yml

# 2. 提交更改
git commit -m "修复baseurl配置，解决样式和链接问题"

# 3. 推送到GitHub
git push
```

## 等待生效

- 推送后，GitHub Pages 需要 2-5 分钟重新构建网站
- 完成后，刷新您的网站页面
- 样式应该会正常显示，链接也应该能正常工作

## 测试链接

修复后，请测试以下链接：
- 首页：https://gearguan.github.io/learning-notes/
- 示例笔记：https://gearguan.github.io/learning-notes/notes/example-note/
- 学习笔记列表：https://gearguan.github.io/learning-notes/notes/
- 关于页面：https://gearguan.github.io/learning-notes/about/

## 如果仍有问题

如果修复后仍有问题，可能需要：
1. 清除浏览器缓存
2. 等待更长时间让GitHub Pages完全更新
3. 检查GitHub仓库的Actions选项卡，确认构建成功 