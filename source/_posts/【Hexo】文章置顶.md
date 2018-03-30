---
title: 【Hexo】文章置顶
date: 2018-03-23 11:50:20
categories:
- Hexo
---

本篇博文主要会谈一谈**如何在 Hexo 中将文章置顶**。

<!-- more -->

## 文章置顶

首先，安装支持文章置顶的软件。打开命令行，输入以下指令：

```bash
npm uninstall hexo-generator-index --save
npm install hexo-generator-index-pin-top --save
```

然后，在需要置顶的文章的 `Front-matter` 中加入 `top: true` 即可。比如，置顶这篇文章的改动如下：

```
---
title: 【数据挖掘比赛】企业经营退出风险预测
date: 2018-02-07 13:06:44
categories:
- 数据挖掘比赛
top: true
---
```

这样就能够将文章置顶了。

## 置顶标志

但是，文章被置顶之后，没有任何置顶标志，这样会让人觉得怪怪的。如何添加置顶标志呢？

打开 `/themes/next/layout/_macro` 目录下的 `post.swig` 文件，定位到 `<div class="post-meta">` 标签下面，插入以下代码：

```html
        {% if post.top %}
          <i class="fa fa-thumb-tack"></i>
          <font color=7D26CD>置顶</font>
          <span class="post-meta-divider">|</span>
        {% endif %}
```

插入的结果如下所示：

```html
        <div class="post-meta">
          {% if post.top %}
            <i class="fa fa-thumb-tack"></i>
            <font color=7D26CD>置顶</font>
            <span class="post-meta-divider">|</span>
          {% endif %}
          <span class="post-time">
```

这样便能添加置顶标志了，最终实现的效果如下：

![置顶文章](/images/top_post.jpg)