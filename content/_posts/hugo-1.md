---
title: Hugo的安装
published: 2025-07-18T15:07:05+08:00
summary: "从Hexo到Hugo的一次迁移"
cover:
  image: "https://t.alcy.cc/moe"
tags: [博客]
categories: '博客'
draft: false 
lang: ''
---
# 安装


# 使用
1. 工具
- `Visual Studio Code`，用于博客的上传
- `网络加速器`，访问Github可能要用

2. Hugo的一些配置

[文件结构介绍看这篇文章](https://www.docx.net.cn/zh-cn/posts/hugo/directory/)





3. Hugo的基本使用

   1. 启动本地预览并创建文档
   ``` bash
   hugo server --buildDrafts --bind 0.0.0.0 --port 1313
   ```
   2. 创建新文章

   ``` bash
   hugo new _posts/first.md
   ```


# 参考
<https://www.afo.im/posts/hugo/>