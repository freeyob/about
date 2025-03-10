---
layout: post
title: "markdown table 中文字符无法对齐"
date: 2025-03-10 10:54:40 +0900
categories: 小问题
---

之前遇到过多次markdown table 中文无法对齐的问题，看着有点难受。

![](/images/markdown_tab.png)

这次有时间就一探究竟。<br>
尝试问各个AI，基本是两个方法:
1. 装格式化插件
2. 找个格式化网站

两个方法都尝试了一下，AI Magic无法解决。<br>
重新尝试google搜索，发现有人也遇到过类似问题：字体的问题，对中文字符支持不好，需要换个支持的字体。下载Sarasa Mono Slab SC字体，再试效果如下：
<!--more-->

![](/images/markdown_tab_solved.png)

对齐问题是解决了，但是字体变的很丑，尝试了系统中所有带“SC”的字体，都很丑，所以又换了回去。宁愿忍受对不齐，也不愿意忍受丑。

后续可能的解决方案：
1. 单独对markdown文件使用“SC”字体。
2. 找个对更好看的字体。
