# 个人技术博客

这是一个基于 Jekyll 的个人技术博客，托管在 GitHub Pages 上。

## 本地开发

### 环境要求

- Ruby 3.2+
- Bundler
- Jekyll 4.4+

### 安装依赖

```bash
# 设置环境变量
export GEM_HOME="$HOME/gems"
export PATH="$HOME/gems/bin:$PATH"

# 安装依赖
bundle install
```

### 启动本地服务器

```bash
# 启动开发服务器
bundle exec jekyll serve

# 访问 http://localhost:4000
```

### 创建新文章

在 `_posts` 目录中创建新文件，文件名格式：`YYYY-MM-DD-title.md`

```markdown
---
layout: post
title:  "文章标题"
date:   2026-04-19 10:30:00 +0800
categories: 分类1 分类2
tags: tag1 tag2 tag3
---

文章内容...
```

## 部署到 GitHub Pages

### 1. 创建 GitHub 仓库

1. 访问 https://github.com/new
2. 创建一个名为 `your-username.github.io` 的仓库
3. 将 `your-username` 替换为你的 GitHub 用户名

### 2. 关联远程仓库

```bash
# 添加远程仓库（替换为你的仓库地址）
git remote add origin https://github.com/your-username/your-username.github.io.git

# 推送到 GitHub
git push -u origin main
```

### 3. 配置 GitHub Pages

1. 访问你的仓库设置页面
2. 进入 "Settings" -> "Pages"
3. 在 "Source" 下选择 "Deploy from a branch"
4. 选择 "main" 分支和 "/ (root)" 目录
5. 点击 "Save"

### 4. 等待部署

GitHub 会自动构建和部署你的网站。几分钟后，你就可以通过 `https://your-username.github.io` 访问你的博客了。

## 配置说明

### 修改 `_config.yml`

```yaml
title: 你的博客标题
email: your-email@example.com
description: >-
  你的博客描述
url: "https://your-username.github.io"
github_username: your-username
author: Your Name
```

### 自定义主题

当前使用 Minima 主题。你可以：

1. 使用其他 Jekyll 主题
2. 自定义 Minima 主题
3. 创建自己的主题

## 目录结构

```
.
├── _config.yml          # 站点配置文件
├── _posts/              # 博客文章目录
├── about.markdown       # 关于页面
├── index.markdown       # 首页
├── 404.html             # 404 页面
├── Gemfile              # Ruby 依赖
└── Gemfile.lock         # 依赖版本锁定
```

## 常用命令

```bash
# 创建新文章
# 手动在 _posts/ 目录创建文件

# 本地预览
bundle exec jekyll serve

# 构建静态网站
bundle exec jekyll build

# 查看帮助
bundle exec jekyll help
```

## 文章写作建议

1. 使用 Markdown 格式
2. 添加适当的分类和标签
3. 使用代码高亮功能
4. 添加图片和链接
5. 定期更新内容

## 代码高亮示例

```python
def hello_world():
    print("Hello, World!")
```

```javascript
function greet(name) {
    console.log(`Hello, ${name}!`);
}
```

## 下一步

- [ ] 修改 `_config.yml` 中的个人信息
- [ ] 创建更多博客文章
- [ ] 自定义主题和样式
- [ ] 添加评论系统（如 Disqus）
- [ ] 配置自定义域名（可选）
- [ ] 添加分析工具（如 Google Analytics）

## 资源链接

- [Jekyll 官方文档](https://jekyllrb.com/docs/)
- [GitHub Pages 文档](https://docs.github.com/en/pages)
- [Minima 主题](https://github.com/jekyll/minima)
- [Markdown 语法指南](https://www.markdownguide.org/)

## 许可证

MIT License

---

祝你写博客愉快！🎉
