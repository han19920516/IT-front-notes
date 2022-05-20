---
title: 01-CSS中的非布局样式
publish: true
---

<ArticleTopAd></ArticleTopAd>

## 前言

CSS中，有很多**非布局样式**，这些样式（属性）和与布局无关，包括：

- 字体、字重、颜色、大小、行高
- 背景、边框
- 滚动、换行
- 装饰性属性（粗体、斜体、下划线）等。


## 文字换行

- ovferflow-wrap：通用的属性。用来说明当一个不能被分开的字符串（单词）太长而不能填充其包裹盒时，为防止其溢出，浏览器是否允许这样的单词**中断换行**。

- word-break：指定了怎样在单词内断行。这里涉及到CJK（英文/日文/韩文）的文字换行。

- white-space：空白处是否换行。

`white-space: nowrap`

如果想换行，可以试试`white-space: pre-wrap`

## CSS 效果

我们可以利用 CSS 实现各种效果，常见的效果属性有：

- box-shadow：盒子的阴影

- text-shadow：文本的阴影

- border-radius

- background

- clip-path


