---
title: 13-CSS3属性：Flex布局图文详解
publish: true
---

<ArticleTopAd></ArticleTopAd>


## 前言

CSS3中的 flex 属性，在布局方面做了非常大的改进，使得我们对**多个元素之间**的布局排列变得十分灵活，适应性非常强。其强大的伸缩性和自适应性，在网页开中可以发挥极大的作用。

### flex 布局的优势

1、**flex 布局的子元素不会脱离文档流**，很好地遵从了“流的特性”。

但你如果用 float 来做布局，float 属性的元素会脱离文档流，而且会涉及到各种 BFC、清除浮动的问题。浮动相关的问题，比较麻烦，所以也成了面试必问的经典题目。但有了 flex 布局之后，这些问题都不存在的。

2、**flex 是一种现代的布局方式，是 W3C 第一次提供真正用于布局的 CSS 规范**。 flex 非常提供了丰富的属性，非常灵活，让布局的实现更佳多样化，且方便易用。

flex 唯一的缺点就在于，它不支持低版本的 IE 浏览器。

### flex 的兼容性问题

上图中可以看到， flex 布局不支持 IE9 及以下的版本；IE10及以上也只是部分支持。如果你的页面不需要处理 IE浏览器的兼容性问题，则可以放心大胆地使用 flex 布局。

### 概念：弹性盒子、子元素

- **弹性盒子**：指的是使用 `display:flex` 或 `display:inline-flex` 声明的**父容器**。

- **子元素/弹性元素**：指的是父容器里面的子元素们（父容器被声明为 flex 盒子的情况下）。

### 概念：主轴和侧轴

弹性盒子里面的子元素们，默认是从左至右排列的，这个方向，代表的就是主轴的方向。

在此，我们引入主轴和侧轴的概念。


- 主轴：flex容器的主轴，默认是水平方向，从左向右。

- 侧轴：与主轴垂直的轴称作侧轴，默认是垂直方向，从上往下。

PS：主轴和侧轴并不是固定不变的，可以通过 `flex-direction` 更换方向.

## 弹性盒子

### 声明定义

使用 `display:flex` 或 `display:inline-flex` 声明一个**父容器**为弹性盒子。此时，这个父容器里的子元素们，会遵循弹性布局。

备注：一般是用 `display:flex`这个属性。`display:inline-flex`用得较少。

### flex-direction 属性

`flex-direction`：用于设置盒子中**子元素**的排列方向。属性值可以是：

| 属性值 | 描述 |
|:-------------|:-------------|
| row | 从左到右水平排列子元素（默认值） |
|column|从上到下垂直排列子元素|
| row-reverse |从右向左排列子元素 |
|column-reverse|从下到上垂直排列子元素|

备注：如果我们不给父容器写`flex-direction`这个属性，那么，子元素默认就是从左到右排列的。

### flex-wrap 属性

`flex-wrap`：控制子元素溢出时的换行处理。

### justify-content 属性

`justify-content`：控制子元素在主轴上的排列方式。

## 弹性元素

### justify-content 属性

- `justify-content: flex-start;` 设置子元素在**主轴上的对齐方式**。属性值可以是：
    - `flex-start` 从主轴的起点对齐（默认值）
    - `flex-end` 从主轴的终点对齐
    - `center` 居中对齐
    - `space-around` 在父盒子里平分
    - `space-between` 两端对齐 平分


### align-items 属性

`align-items`：设置子元素在**侧轴上的对齐方式**。属性值可以是：
    - `flex-start` 从侧轴开始的方向对齐
    - `flex-end` 从侧轴结束的方向对齐
    - `baseline` 基线 默认同flex-start
    - `center` 中间对齐
    - `stretch` 拉伸

### `flex`属性：设置子盒子的权重

代码演示：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        *{
            margin: 0;
            padding: 0;
            list-style:none;
        }
        body{
            background-color: #eee;
            font-family: "Microsoft Yahei";

        }
        section{
            width: 1000px;
            margin:50px auto;
        }
        section h3{
            font-size:22px;
            font-weight: normal;
        }

        ul{
            border: 1px solid #999;
            background-color: #fff;
            display: flex;

        }

        ul li{
            width: 200px;
            height: 200px;
            background: pink;
            margin:10px;

        }

        section:nth-child(1) ul li:nth-child(1){
            flex:1;
        }

        section:nth-child(1) ul li:nth-child(2){
            flex:1;
        }

        section:nth-child(1) ul li:nth-child(3){
            flex:8;
        }

        section:nth-child(2) ul li:nth-child(1){

        }

        section:nth-child(2) ul li:nth-child(2){
            flex:1;
        }

        section:nth-child(2) ul li:nth-child(3){
           flex:4;
        }


    </style>
</head>
<body>
<section>
    <h3>伸缩比例:flex</h3>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
    </ul>
</section>

<section>
    <h3>伸缩比例:flex</h3>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
    </ul>
</section>


</body>
</html>
```

## 相关链接

### CSS Flexbox 可视化手册


-  CSS Flexbox Fundamentals Visual Guide：<https://medium.com/swlh/css-flexbox-fundamentals-visual-guide-1c467f480dac>

###  flex 相关的推荐文章

- flex 效果在线演示：<https://demos.scotch.io/visual-guide-to-css3-flexbox-flexbox-playground/demos/>

- A Complete Guide to Flexbox | 英文原版：<https://css-tricks.com/snippets/css/a-guide-to-flexbox/>

## 技巧：使用 flex:1 auto 自动撑满剩余空间






