---
title: 06-CSS盒模型详解
publish: true
---

<ArticleTopAd></ArticleTopAd>


## 盒子模型

### 前言

无论是div、span、还是a都是盒子。

但是，图片、表单元素一律看作是文本，它们并不是盒子。这个很好理解，比如说，一张图片里并不能放东西，它自己就是自己的内容。

### 盒子中的区域

一个盒子中主要的属性就5个：width、height、padding、border、margin。如下：

- width和height：**内容**的宽度、高度（不是盒子的宽度、高度）。
- padding：内边距。
- border：边框。
- margin：外边距。

注意：**宽度和真实占有宽度，不是一个概念！**来看下面这例子。

### 标准盒模型和IE盒模型

在 CSS 盒子模型 (Box Model) 规定了元素处理元素的几种方式：
- width和height：**内容**的宽度、高度（不是盒子的宽度、高度）。
- padding：内边距。
- border：边框。
- margin：外边距。

CSS盒模型和IE盒模型的区别：

- 在 <font color="#0000FF">**标准盒子模型**</font>中，<font color="#0000FF">**width 和 height 指的是内容区域**</font>的宽度和高度。增加内边距、边框和外边距不会影响内容区域的尺寸，但是会增加元素框的总尺寸。

- <font color="#0000FF">**IE盒子模型**</font>中，<font color="#0000FF">**width 和 height 指的是内容区域+border+padding**</font>的宽度和高度。

### `<body>`标签也有margin

浏览器给`<body>`默认的margin大小是8个像素，此时`<body>`占据了整个页面的一大部分区域，而不是全部区域

## 认识width、height

一定要知道，在前端开发工程师眼中，世界中的一切都是不同的。


下面这两个盒子，真实占有宽高，都是302*302：

盒子1：

```css
.box1{
	width: 100px;
	height: 100px;
	padding: 100px;
	border: 1px solid red;
}
```

盒子2：

```css
.box2{
	width: 250px;
	height: 250px;
	padding: 25px;
	border: 1px solid red;
}
```

真实占有宽度 = 左border + 左padding + width + 右padding + 右border



**如果想保持一个盒子的真实占有宽度不变，那么加width的时候就要减padding。加padding的时候就要减width**。因为盒子变胖了是灾难性的，这会把别的盒子挤下去。


## 认识padding

### padding区域也有颜色

padding就是内边距。padding的区域有背景颜色，css2.1前提下，并且背景颜色一定和内容区域的相同。也就是说，background-color将填充**所有border以内的区域。**


### padding有四个方向

padding是4个方向的，所以我们能够分别描述4个方向的padding。

方法有两种，第一种写小属性；第二种写综合属性，用空格隔开。

小属性的写法：

```css
	padding-top: 30px;
	padding-right: 20px;
	padding-bottom: 40px;
	padding-left: 100px;
```

综合属性的写法：(上、右、下、左)（顺时针方向，用空格隔开。margin的道理也是一样的）

```css
padding:30px 20px 40px 100px;
```

如果写了四个值，则顺序为：上、右、下、左。

如果只写了三个值，则顺序为：上、右和左、下。

如果只写了两个值，则顺序为：上和下、左和右。

比如说：

```
padding: 30px 40px;
```

则顺序等价于：30px 40px 30px 40px;

要懂得，**用小属性层叠大属性**。比如：

```
padding: 20px;
padding-left: 30px;
```

### 一些元素，默认带有padding

我们做站的时候，为了便于控制，总是喜欢清除这个默认的padding。

可以使用`*`进行清除：

```css
		*{
			margin: 0;
			padding: 0;
		}
```

但是，`*`的效率不高，所以使用并集选择器，罗列所有的标签（CSS RESETS）：

```
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,code,form,fieldset,legend,input,textarea,p,blockquote,th,td{
    margin:0;
    padding:0;
}
```

## 认识border

border就是边框。边框有三个要素：像素（粗细）、线型、颜色。

比如：

```css

.div1{
	width: 10px;
	height: 10px;
	border: 2px solid red;
}

```

颜色如果不写，默认是黑色。另外两个属性如果不写，则无法显示边框。

### border-style

`border:10px ridge red;`这个属性，在chrome和firefox、IE中有细微差别：（因为可以显示出效果，因此并不是兼容性问题，只是有细微差别而已）

比较稳定的border-style就几个：solid、dashed、dotted。

### border拆分

border是一个大综合属性。比如说：

```css
border:1px solid red;
```

就是把上下左右这四个方向的边框，都设置为 1px 宽度、线型实线、red颜色。


border属性是能够被拆开的，有两大种拆开的方式：

- （1）按三要素拆开：border-width、border-style、border-color。（一个border属性是由三个小属性综合而成的）

- （2）按方向拆开：border-top、border-right、border-bottom、border-left。

**一个border属性，是由三个小属性综合而成的**。如果某一个小属性后面是空格隔开的多个值，那么就是上右下左的顺序。举例如下：

（1）按三要素拆：

```css
border-width:10px;    //边框宽度
border-style:solid;   //线型
border-color:red;     //颜色。
```
等价于：

```
border:10px solid red;
```

(2)按方向来拆：

```css
border-top:10px solid red;
border-right:10px solid red;
border-bottom:10px solid red;
border-left:10px solid red;
```

等价于：

```css
border:10px solid red;
```

（3）按三要素和方向来拆：(就是把每个方向的，每个要素拆开。3*4 = 12)

```css
	border-top-width:10px;
	border-top-style:solid;
	border-top-color:red;
	border-right-width:10px;
	border-right-style:solid;
	border-right-color:red;
	border-bottom-width:10px;
	border-bottom-style:solid;
	border-bottom-color:red;
	border-left-width:10px;
	border-left-style:solid;
	border-left-color:red;
```

等价于：

```css
border:10px solid red;

```
```css
border:10px solid red;
border-style:solid dashed;
```
border可以没有：

```css
border:none;
```

可以某一条边没有：

```css
border-left: none;
```

也可以调整左边边框的宽度为0：

```css
border-left-width: 0;
```

### border-image 属性


```css
border-image: url(.img.png) 30 round;
```

### 举例1：利用 border 属性画一个三角形（小技巧）

完整代码如下：

```css
div{
	width: 0;
	height: 0;
	border: 50px solid transparent;
	border-top-color: red;
	border-bottom: none;
}

```

### 举例2：利用 border 属性画一个三角形

（用 css 画等边三角形）

```css
.div1{
	width: 0;
	height: 0;
	border-top: 30px solid red;
	/* 通过改变 border-left 和 border-right 中的像素值，来改变三角形的形状 */
	border-left: 20px solid transparent;
	border-right: 20px solid transparent;
}

```



