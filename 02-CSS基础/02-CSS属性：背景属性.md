---
title: 02-CSS属性：背景属性
publish: true
---

<ArticleTopAd></ArticleTopAd>


## background 的常见背景属性


**css2.1** 中，常见的背景属性有以下几种：（经常用到，要记住）

- `background-color:#ff99ff;`  设置元素的背景颜色。

- `background-image:url(images/2.gif);` 将图像设置为背景。

-  `background-repeat: no-repeat;`  设置背景图片是否重复及如何重复，默认平铺满。（重要）
	- `no-repeat`不要平铺；
	- `repeat-x`横向平铺；
	- `repeat-y`纵向平铺。

- `background-position:center top;` 设置背景图片在当前容器中的位置。

- `background-attachment:scroll;` 设置背景图片是否跟着滚动条一起移动。
属性值可以是：`scroll`（与fixed属性相反，默认属性）、`fixed`（背景就会被固定住，不会被滚动条滚走）。

- 综合属性`background`，它的作用是：将上面的多个属性写在一个声明中。

**CSS3** 中，新增了一些background属性：

- background-origin

- background-clip 背景裁切

- background-size 调整尺寸

- 多重背景


## background-color：背景颜色的表示方法

css2.1 中，颜色的表示方法有三种：单词、rgb表示法、十六进制表示法。

红色可以有下面的三种表示方法：

```css
	background-color: red;
	background-color: rgb(255,0,0);
	background-color: #ff0000;
```

CSS3 中，有一种新的表示颜色的方式：RGBA或者HSLA。

RGBA、HSLA可应用于**所有**使用颜色的地方。

### 用英语单词表示

能够用英语单词来表述的颜色，都是简单颜色，比如red、green、blue、orange、gray等。

```css
background-color: red;
```
### RGB 表示法

RGB 表示三原色“红”red、“绿”green、“蓝”blue。

光学显示器中，每个像素都是由三原色的发光原件组成的，靠明亮度不同调成不同的颜色的。r、g、b的值，每个值的取值范围0~255，一共256个值。

红色：

```css
background-color: rgb(255,0,0);
```

黑色：

```css
background-color: rgb(0,0,0);
```

黄色就是红色和绿色的叠加：

```css
background-color: rgb(255,255,0);
```

### RGBA 表示法

```javascript
    background-color: rgba(0, 0, 255, 0.3);

    border: 30px solid rgba(0, 255, 0, 0.3);
```

**代码解释**：

- RGBA 即：Red 红、Green 绿、Blue 蓝、Alpha 透明度。

- R、G、B 的取值范围是：0~255；透明度的取值范围是 0~1。

**RGB色彩模式：**

 - 自然界中绝大部分颜色都可以用红、绿、蓝(RGB)这三种颜色波长的不同强度组合而得,三原色原理。
 - RGB三原色也叫加色模式，把不同光的波长加到一起的时候，可以得到不同的混合色。例：红+绿=黄色，红+蓝＝紫色，绿+蓝=青。
 - RGB各有256级(0-255)亮度，256级的RGB色彩总共能组合出约1678万种色彩，即256×256×256=16777216。

 在数字视频中，对RGB三基色各进行8位编码就构成了大约1678万种颜色，这就是我们常说的真彩色。所有显示设备都采用的是RGB色彩模式。

### 十六进制表示法

比如红色：

```
background-color: #ff0000;
```

所有用`#`开头的色值，都是16进制的。

- #ff0000等于rgb(255,0,0)。

- `background-color: #123456;`等价于`background-color: rgb(18,52,86);`

**十六进制可以简化为3位，所有#aabbcc的形式，能够简化为#abc**。

几种常见的颜色简写
```
	#000   黑
	#fff   白
	#f00   红
	#222   深灰
	#333   灰
	#ccc   浅灰
```

### HSLA 表示法

举例：

```javascript
	background-color: hsla(240,50%,50%,0.4);
```

- `H` 色调，取值范围 0~360。0或360表示红色、120表示绿色、240表示蓝色。

- `S` 饱和度，取值范围 0%~100%。值越大，越鲜艳。

- `L` 亮度，取值范围 0%~100%。亮度最大时为白色，最小时为黑色。

- `A` 透明度，取值范围 0~1。


**关于设置透明度的其他方式：**

（1）`opacity: 0.3;` 会将整个盒子及子盒子设置透明度。也就是说，当盒子设置半透明的时候，会影响里面的子盒子。

（2）`background: transparent;` 可以单独设置透明度，但设置的是完全透明（不可调节透明度）。

## `background-repeat`属性

`background-repeat:no-repeat;`设置背景图片是否重复及如何重复，默认平铺满。属性值可以是：

- `no-repeat`（不要平铺）
- `repeat-x`（横向平铺）
- `repeat-y`（纵向平铺）


## `background-position`属性

`background-position`属性指的是**背景定位**属性。公式如下：

在描述属性值的时候，有两种方式：用像素描述、用单词描述。

**1、用像素值描述属性值：**

格式如下：

```
	background-position:向右偏移量 向下偏移量;
```

属性值可以是正数，也可以是负数。比如：`100px 200px`、`-50px -120px`。


**2、用单词描述属性值：**

格式如下：

```
	background-position: 描述左右的词 描述上下的词;
```

- 描述左右的词：left、center、right
- 描述上下的词：top 、center、bottom

`right center`表示将图片放到右边的中间；`center center`表示将图片放到正中间。

`bottom`表示图片的底边和父亲**底边贴齐**（好好理解）。

```
        body{
            background-image: url(/Users/smyhvae/Dropbox/img/20170812_1950.jpg);
            background-repeat: no-repeat;
            background-position: center top;
        }
```

（通栏banner）

将banner图作为div的背景图，这样的话，背景图超出div的部分，会自动移溢出。需要给div设置的属性如下：

```css
        div{
            height: 465px;
            background-image: url(http://img.smyhvae.com/20170813_1053.jpg);
            background-position: center top;
            background-repeat: no-repeat;
        }
```

## background-attachment 属性

- `background-attachment:scroll;` 设置背景图片是否固定。属性值可以是：
	- `fixed`（背景就会被固定住，不会被滚动条滚走）。
	- `scroll`（与fixed属性相反，默认属性）

### background 综合属性

举例1:

```css
	background:red url(1.jpg) no-repeat 100px 100px fixed;
```

等价于：

```css
	background-color:red;
	background-image:url(1.jpg);
	background-repeat:no-repeat;
	background-position:100px 100px;
	background-attachment:fixed;
```

```css
	background: blue url(images/wuyifan.jpg) no-repeat 100px 100px;
```

## `background-size`属性：背景尺寸

`background-size`属性：设置背景图片的尺寸。

格式举例：

```javascript
	/* 宽、高的具体数值 */
	background-size: 500px 500px;

	/* 宽高的百分比（相对于容器的大小） */
	background-size: 50% 50%;   // 如果两个属性值相同，可以简写成：background-size: 50%;

	background-size: 100% auto;  //这个属性可以自己试验一下。

	/* cover：图片始终填充满容器，且保证长宽比不变。图片如果有超出部分，则超出部分会被隐藏。 */
	background-size: cover;

	/* contain：将图片完整地显示在容器中，且保证长宽比不变。可能会导致容器的部分区域为空白。  */
	background-size: contain;
```

- `cover`：图片始终**填充满**容器，且保证**长宽比不变**。图片如果有超出部分，则超出部分会被隐藏。

- `contain`：将图片**完整地**显示在容器中，且保证**长宽比不变**。可能会导致容器的部分区域留白。

## 背景原点：`background-origin` 属性

`background-origin` 属性：控制背景从什么地方开始显示。

格式举例：

```javascript

	/* 从 padding-box 内边距开始显示背景图 */
	background-origin: padding-box;           //默认值

	/* 从 border-box 边框开始显示背景图  */
	background-origin: border-box;

	/* 从 content-box 内容区域开始显示背景图  */
	background-origin: content-box;

```

## `background-clip`属性：设置元素的背景（背景图片或颜色）是否延伸到边框下面

格式举例：

`background-clip: content-box;`   超出的部分，将裁剪掉。属性值可以是：

 - `border-box` 超出 border-box 的部分，将裁剪掉

 - `padding-box` 超出 padding-box 的部分，将裁剪掉

 - `content-box` 超出 content-box 的部分，将裁剪掉

假设现在有这样的属性设置：

```javascript
	background-origin: border-box;

	background-clip: content-box;
```

背景图片从**边框部分**开始加载，但是呢，超出**内容区域**的部分将被裁减掉。

## 同时设置多个背景

我们可以给一个盒子同时设置多个背景，用以逗号隔开即可。可用于自适应局。

代码举例：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        .box {
            height: 416px;
            border: 1px solid #000;
            margin: 100px auto;
            /* 给盒子加多个背景，按照背景语法格式书写，多个背景使用逗号隔开 */
            background: url(images/bg1.png) no-repeat left top,
            url(images/bg2.png) no-repeat right top,
            url(images/bg3.png) no-repeat right bottom,
            url(images/bg4.png) no-repeat left bottom,
            url(images/bg5.png) no-repeat center;
        }
    </style>
</head>
<body>
<div class="box"></div>
</body>
</html>
```

## 渐变：background-image

渐变是CSS3当中比较丰富多彩的一个特性，通过渐变可以实现许多炫丽的效果，有效的减少图片的使用数量，并且具有很强的适应性和可扩展性。

渐变分为：

- 线性渐变：沿着某条直线朝一个方向产生渐变效果。

- 径向渐变：从一个**中心点**开始沿着**四周**产生渐变效果。

- 重复渐变。


### 线性渐变

格式：

```javascript

    background-image: linear-gradient(方向, 起始颜色, 终止颜色);

    background-image: linear-gradient(to right, yellow, green);
```

参数解释：

- 方向可以是：`to left`、`to right`、`to top`、`to bottom`、角度`30deg`（指的是顺时针方向30°）。

### 径向渐变

格式：

```
	background-image: radial-gradient(辐射的半径大小, 中心的位置, 起始颜色, 终止颜色);

	background-image: radial-gradient(100px at center,yellow ,green);

```

解释：围绕中心点做渐变，半径是150px，从黄色到绿色做渐变。

中心点的位置可以是：at  left  right  center bottom  top。如果以像素为单位，则中心点参照的是盒子的左上角。

当然，还有其他的各种参数。格式举例：

```html

        /*辐射半径为100px，中心点在中间*/
        div:nth-child(1) {
            background-image: radial-gradient(100px at center, yellow, green);
        }

        /*中心点在左上角*/
        div:nth-child(3) {
            background-image: radial-gradient(at left top, yellow, green);
        }

        div:nth-child(2) {
            background-image: radial-gradient(at 50px 50px, yellow, green);
        }

        /*设置不同的颜色渐变*/
        div:nth-child(4) {
            background-image: radial-gradient(100px at center,
            yellow 0%,
            green 30%,
            blue 60%,
            red 100%);
        }

        /*如果辐射半径的宽高不同，那就是椭圆*/
        div:nth-child(5) {
            background-image: radial-gradient(100px 50px at center, yellow, green);
        }

```

## clip-path：裁剪出元素的部分区域做展示

`clip-path`属性可以创建一个只有元素的部分区域可以显示的剪切区域。区域内的部分显示，区域外的隐藏。

举例：（鼠标悬停时，放大裁剪的区域）

```css
    .div1 {
        width: 320px;
        height: 320px;
        border: 1px solid red;
        background: url(http://images/sss.jpg) no-repeat;
        background-size: cover;

        /* 裁剪出圆形区域 */
        clip-path: circle(50px at 100px 100px);
        transition: clip-path .4s;
    }
    .div1:hover{
        /* 鼠标悬停时，裁剪出更大的圆形 */
        clip-path: circle(80px at 100px 100px);
    }
```

`clip-path`属性的好处是，即使做了任何裁剪，**容器的占位大小是不变的**。比如上方代码中，容器的占位大小一直都是 320px * 320px。

