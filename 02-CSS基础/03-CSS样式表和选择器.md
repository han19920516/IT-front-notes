---
title: 03-CSS样式表和选择器
publish: true
---

<ArticleTopAd></ArticleTopAd>

## 本文主要内容

-   CSS 概述
-   CSS 和 HTML 结合的三种方式：`行内样式表`、`内嵌样式表`、`外部样式表`
-   CSS 四种基本选择器：`标签选择器`、`类选择器`、`ID选择器`、`通用选择器`
-   CSS 几种扩展选择器：`后代选择器`、`交集选择器`、`并集选择器`
-   CSS 样式优先级

## 前言

## CSS 概述

CSS：Cascading Style Sheet，层叠样式表。CSS 的作用就是给 HTML 页面标签添加各种样式，**定义网页的显示效果**。简单一句话：CSS 将网页**内容和显示样式进行分离**，提高了显示功能。

为什么要使用 CSS。

**HTML 的缺陷：**

1. 不能够适应多种设备
2. 要求浏览器必须智能化足够庞大
3. 数据和显示没有分开
4. 功能不够强大

**CSS 优点：**

1. 使数据和显示分开
2. 降低网络流量
3. 使整个网站视觉效果一致
4. 使开发效率提高了（耦合性降低，一个人负责写 html，一个人负责写 css）


### CSS 的重点知识点

盒子模型、浮动、定位

css 对换行不敏感，对空格也不敏感。但是一定要有标准的语法。冒号，分号都不能省略。

## CSS 语法

**语法格式：**（其实就是键值对）

```html
选择器{ 属性名: 属性值; 属性名: 属性值; }
```

或者可以写成：

```css
选择器 {
    k: v;
    k: v;
    k: v;
    k: v;
}
选择器 {
    k: v;
    k: v;
    k: v;
    k: v;
}
```
**解释：**

-   选择器代表页面上的某类元素，选择器后一定是大括号。
-   属性名后必须用冒号隔开，属性值后用分号（最后一个属性可以不用分号，但最好还是加上分号）。
-   冒号和属性值之间可以留一个空格（编程习惯的经验）。
-   如果一个属性有多个值的话，那么多个值用**空格**隔开。

### css 代码的注释

**格式：**

```html
<style type="text/css">
    /*
		具体的注释
	*/

    p {
        font-weight: bold;
        font-style: italic;
        color: red;
    }
</style>
```

## CSS 的一些简单常见的属性


**字体颜色：**（c）

```html
color:red;
```

color 属性的值，可以是英语单词，比如 red、blue、yellow 等等；也可以是 rgb、十六进制(后期详细讲)。

**字号大小：**（fos）

```html
font-size:40px;
```

font 就是“字体”，size 就是“尺寸”。px 是“像素”。单位必须加，不加不行。

**背景颜色：**（bgc）

```html
background-color: blue;
```

background 就是“背景”。

**加粗：**（fwb）

```html
font-weight: bold;
```

font 是“字体” weight 是“重量”的意思，bold 粗。

**不加粗：**（fwn）

```html
font-weight: normal;
```

normal 就是正常的意思。

**斜体：**（fsi）

```html
font-style: italic;
```

italic 就是“斜体”。

**不斜体：**（fsn）

```html
font-style: normal;
```

**下划线：**（tdu）

```html
text-decoration: underline;
```

decoration 就是“装饰”的意思。

**没有下划线：**（tdn）

```html
text-decoration:none;
```

## CSS 的书写方式

CSS 代码理论上的位置是任意的，**但通常写在`<style>`标签里**。

CSS 的书写方式有三种：

1. **行内样式**：在某个特定的标签里采用 style **属性**。范围只针对此标签。

2. **内嵌样式**（内联样式）：在页面的 head 标签里里采用`<style>`**标签**。范围针对此页面。
3. **外链样式**：引入外部样式表 CSS **文件**。这种引入方式又分为两种：
   - 3.1 采用`<link>`标签。例如：`<link rel = "stylesheet" type = "text/css" href = "a.css"></link>`
   - 3.2 采用 import 导入，必须写在`<style>`标签中。然后用类似于`@import url(a.css) ;`这种方式导入。


### 1、CSS 和 HTML 结合方式一：行内样式

采用 style 属性。范围只针对此标签适用。

该方式比较灵活，但是对于多个相同标签的同一样式定义比较麻烦，适合局部修改。


### 2、CSS 和 HTML 结合方式二：内嵌样式表

在 head 标签中加入`<style>`标签，对多个标签进行统一修改，范围针对此页面。

该方式可以对单个页面的样式进行统一设置，但对于局部不够灵活。



### 3、CSS 和 HTML 结合方式三：引入外部样式表 css 文件

**引入样式表文件**的方式又分为两种：

-   （1）**采用`<link>`标签**。例如：`<link rel = "stylesheet" type = "text/css" href = "a.css"></link>`

-   （2）**采用 import**，必须写在`<style>`标签中，并且必须是第一句。例如：`@import url(a.css) ;`

> 两种引入样式方式的区别：外部样式表中不能写<link>标签，但是可以写 import 语句。


**`<link>`标签的 rel 属性：**。其属性值有以下两种：

-   `stylesheet`：定义的样式表
-   `alternate stylesheet`：候选的样式表

```html
  <link rel = "stylesheet" type = "text/css" href = "a.css"></link>
  <link rel = "alternate stylesheet" type = "text/css" href = "b.css" title="第二种样式"></link>
  <link rel = "alternate stylesheet" type = "text/css" href = "c.css" title="第三种样式"></link>
```

## CSS 的四种基本选择器

CSS 选择器：就是指定 CSS 要作用的标签，那个标签的名称就是选择器。意为：选择哪个容器。

CSS 的选择器分为两大类：基本选择器和扩展选择器。

**基本选择器：**

-   标签选择器：针对**一类**标签
-   ID 选择器：针对某**一个**特定的标签使用
-   类选择器：针对**你想要的所有**标签使用
-   通用选择器（通配符）：针对所有的标签都适用（不建议使用）

## CSS 的几种高级选择器

**高级选择器：**

-   后代选择器：用空格隔开
-   交集选择器：选择器之间紧密相连
-   并集选择器（分组选择器）：用逗号隔开
-   伪类选择器

