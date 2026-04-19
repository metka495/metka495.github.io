---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

欢迎来到我的技术博客！

这里是分享编程技术、开发经验和学习笔记的地方。我会在这里发布关于软件开发、编程技巧、工具使用等方面的文章。

## 最新文章

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%Y-%m-%d" }}
{% endfor %}

## 关于这个博客

这个博客使用 Jekyll 静态网站生成器构建，托管在 GitHub Pages 上。主要关注：

- 编程语言和技术栈
- 开发工具和工作流程
- 最佳实践和设计模式
- 技术问题和解决方案

希望我的分享能对你有所帮助！
