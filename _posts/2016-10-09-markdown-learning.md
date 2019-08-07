---
layout: post
title: Markdown基本知识学习
tags: [writing]
---

今天第一次使用Markdown，被它的效果深深地感动了。之前电脑安装了Markdown编辑器 — MarkdownPad2，但因为种种原因没有去使用。今天在看魏剑锋的微信公众号文章时，看到了几篇关于写作相关的文章，就想到了之前下载MarkdownPad2就是因为想写博客，于是就去尝试着用了一下。

那么，现在问题来了，怎样去学这个Markdown呢？因为最近经常使用思维导图去学习总结，所以我先用思维导图去总结了一下学习Markdown的几个问题：
- Markdown是什么？
- 为什么要用Markdown？
- 如何使用Markdown？

## 1. Markdown是什么？
> Markdown is a lightweight markup language with plain text formatting syntax designed so that it can be converted to HTML and many other formats using a tool by the same name. (Wikipedia)

## 2. 为什么要用Markdown？
可以看看使用Markdown有哪些好处：
- 纯文本，所以兼容性极强，可以用所有文本编辑器打开
- 让你专注于文字而不是排版
- 格式转换方便，Markdown 的文本你可以轻松转换为 html、电子书等
- Markdown 的标记语法有极好的可读性

## 3. 如何使用Markdown？
### 3.1 Markdown的基本语法
- 标题：#
- 列表：-
- 链接和图片
 - 链接：\[显示文本](链接地址)
 - 图片：\!\[](图片链接地址)
- 引用：>
- 粗体和斜体
 - 粗体：用两个\*或_包含一段文本，例：\*\*一盏灯\*\*，__一盏灯__
 - 斜体：用一个\*或_包含一段文本，例：\*一盏灯\*，_一盏灯_
- 代码引用
 - 引用的语句只有一段，不分行，则用 ` 将语句包起来
 - 引用的语句为多行，则将```置于这段代码的首行和末行
- 分割线：用三个\*或-表示，即\***或---
- 表格
- 显示链接中带括号的图片

### 3.2 Markdown的编辑器
- Windows平台推荐[MarkdownPad](http://markdownpad.com/)
- Mac平台推荐[Mou](http://mouapp.com/)
- 其它推荐[Atom](https://atom.io/)

Atom 与 Markdown 相关的插件
> **markdown-preview**：markdown预览
> **markdown-scroll-sync**：实时滚动预览插件
> **tidy markdown**：美化markdown显示
>**markdown-preview-opener**：当打开一个markdown文件时，自动打开预览界面
> **markdown-pdf**
> **markdown-toc**
> **markdown-writer**
> **atomic chrome**：让公众号使用markdown发表文章成为可能


### 3.3 相关资源
- [献给写作者的 Markdown 新手指南](http://www.jianshu.com/p/q81RER/)
- [Markdown 语法说明 (简体中文版)](http://wowubuntu.com/markdown/)
- [Learning-Markdown (Markdown 入门参考)](http://xianbai.me/learn-md/index.html)
- [Markdown写作浅谈](http://www.jianshu.com/p/PpDNMG)
- [好用的Markdown编辑器一览](http://www.williamlong.info/archives/4319.html)
- [可能是目前最全面的Markdown写作解决方案](https://zhuanlan.zhihu.com/p/21694467)
- [Atom：优雅迷人的编辑神器](http://www.jianshu.com/p/b4c8479cfaa5)
- [Atom 新一代编辑神器](http://www.jianshu.com/p/eda116972d70)
- [atom编辑器的使用和markdown基本语法](http://www.jianshu.com/p/f3fd881548ad)
- [Atom Flight Manual](http://flight-manual.atom.io/getting-started/sections/why-atom/)
- [markdown-preview-plus (Github)](https://github.com/Galadirith/markdown-preview-plus)

### 3.4 实战
为了掌握Markdown语法，我选取了两个例子作为我的练习。一个是“[Awesome Reinforcement Learning](https://github.com/aikorea/awesome-rl)”，主要是分析它的md文件；另一个是“[Markdown写作浅谈](http://www.jianshu.com/p/PpDNMG)”，主要是根据前面所学到的知识在简书上复现出这篇文章。
