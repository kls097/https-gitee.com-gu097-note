# CSS学习笔记

# 1 CSS 介绍

## 1.1 HTML + CSS +JavaScript = 结构 + 表现 + 交互

## 1.2 如何学习

### 1.2.1 CSS 是什么

Cascading Style Sheet 层叠级联样式表

CSS：表现（美化网页）

字体、颜色、边距、高度、宽度、背景图片、网页定位、网页浮动...



### 1.2.2 CSS 怎么用（快速入门）

### 1.2.3 CSS 选择器（重点 + 难点）

### 1.2.4 美化网页（文字、阴影、超链接、列表、渐变...）

### 1.2.5 盒子模型

### 1.2.6 浮动

### 1.2.7 定位

### 1.2.8 网页动画（特效效果）

# 2 CSS 发展史

CSS1.0 只能使用一些基本的如字体加粗等

CSS2.0 DIV（块） + CSS，HTML 与 CSS 结构分离的思想，网页变得简单，SEO（搜索引擎优化）

CSS2.1 浮动、定位

CSS3.0 圆角、阴影、动画... 浏览器兼容问题

# 3 CSS 的快速入门及优势

## 3.1 CSS 两种写法

```
<link rel="stylesheet" href="../CSS/style.css">

<style>
  h1 {
    color: red;
  }
</style>
```

## 3.2 CSS 的优势

1. 内容和表现分离
2. 网页结构表现统一，可以实现复用
3. 样式十分的丰富
4. 建议使用独立于 html 的 css 文件
5. 利于SEO，容易被搜索引擎录入

# 4 三种 CSS 导入方式

1. 内部样式（标签内部）
2. 行内样式（style代码块）
3. 外部样式（css文件）

优先级：就近原则，谁离元素越近，就是用他

拓展：外部样式两种写法

- 链接式：

```
<link rel="stylesheet" href="../CSS/style.css">
```

- 导入式：CSS2.1 特有！

```
<style>
  @import url("../CSS/style.css");
</style>
```

# 5 选择器

## 5.1 选择器的作用

选择页面上某一个或者某一类元素

## 5.2 基本选择器

1. 标签选择器 用标签名
2. 类选择器 用.class名称
3. id选择器 用#id名称
4. \* 通配

优先级：id选择器 > class选择器 > 标签选择器

## 5.3 层次选择器

1. 后代选择器 在某个元素的后面 所有后代

```
body p {
  color: red;
}
```

1. 子选择器 一代 儿子

```
body>p {
  color: red;
}
```

1. 相邻兄弟选择器 下一个兄弟（只有一个，并且是同级下一个）

```
.active+p {
  color: red;
}
```

1. 通用选择器 下面的所有同级元素

```
.active~p {
  color: red;
}
```

## 5.4 结构伪类选择器

伪类：条件、特效

```
ul li:first-child {
    color: red;
}
ul li:last-child {
    color: greenyellow;
}
/*选择当前p元素的父级元素，选中父级元素的第一个标签*/
p:nth-child(1) {
    color: red;
}
/*选中当前元素的父级元素下的第一个p标签*/
p:nth-of-type(1) {
    color: red;
}
.active:hover {
    background: black;
}
```

## 5.5 属性选择器

```
/*[]里面填写属性名，或者属性名=属性值(正则)*/
a[id] {
    color: red;
}
a[id=first] {
    color: red;
}
/*
    =是绝对等于
    *=是包含等于
*/
a[class="first"] {
    color: red;
}
a[class*="first"] {
    color: black;
}
/*以...来头*/
a[href^=http] {
    color: red;
}
/*以...结尾$*/
a[href$=com] {
    color: black;
}
```

# 6 CSS 样式及字体样式

## 6.1 为什么要美化网页

1. 有效的传递页面信息
2. 美化网页、页面漂亮，才能吸引用户
3. 凸显页面的主题
4. 提高用户的体验 

span标签：重点要突出的字，使用span套起来

## 6.2 字体样式

```
body {
    /*字体*/
    font-family: "Microsoft YaHei UI";
    /*字体大小*/
    font-size: 14px;
    /*字体粗细*/
    font-weight: bold;
    /*字体颜色*/
    color: red;
    /*字体风格 字体粗细 字体大小/字体行高 字体*/
    font: oblique bold 14px/50px "Microsoft YaHei UI";
}
```

## 6.3 文本样式

```
span {
    /*单词*/
    color: red;
    /*RGB red green blue 0~F*/
    color: #FF0000;
    color: rgb(255, 0, 0);
    color: #00FF00;
    color: rgb(0, 255, 0);
    color: #0000FF;
    color: rgb(0, 0, 255);
    /*RGBA red green blue 0~F a是Alpha 透明度0~1*/
    color: rgba(0, 0, 255, 0.1);
    /*排版*/
    text-align: center;
    /*首行缩进*/
    text-indent: 2em;
    /*块高度*/
    height: 300px;
    /*行高 当块高度和行高一致的时候，就实现了垂直居中*/
    line-height: 300px;
    /*下划线*/
    text-decoration: underline;
    /*中划线*/
    text-decoration: line-through;
    /*上划线*/
    text-decoration: overline;
}
/*图片垂直居中*/
img {
    vertical-align: middle;
}
/*超链接去下划线*/
a {
    text-decoration: none;
}
```

# 7 文本阴影和超链接伪类

## 7.1 超链接伪类

```
a {
    text-decoration: none;
    color: #000000;
}
/*鼠标悬停*/
a:hover {
    color: red;
}
/*鼠标激活，按住不放*/
a:active {
    color: orange;
}
```

## 7.2 文本阴影

```
/*文本阴影 水平偏移 垂直偏移 阴影半径 颜色*/
#price {
    text-shadow: 10px 10px 2px red;
}
```

# 8 背景图片及渐变

## 8.1 背景图片

```
div {
    /*背景颜色 背景图片 图片位置 图片平铺方式*/
    background: red url("../IMG/img.JPG") 200px 100px no-repeat;
    /*默认背景图片平铺*/
    background-image: url("../IMG/img.JPG");
    /*默认背景图片水平平铺*/
    background-repeat: repeat-x;
    /*默认背景图片垂直平铺*/
    background-repeat: repeat-y;
    /*默认背景图片不平铺*/
    background-repeat: no-repeat;
    /*背景图片的位置*/
    background-position: 200px 200px;
}
```

## 8.2 渐变

```
div {
    /*渐变网站查找*/
    background: #ee9ca7;  /* fallback for old browsers */
    background: -webkit-linear-gradient(to right, #ffdde1, #ee9ca7);  /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(to right, #ffdde1, #ee9ca7); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}
```

# 9 盒子模型及边框使用

## 9.1 边框

### 9.1.1 边框的粗细

### 9.1.2 边框的样式

### 9.1.3 边框的颜色

```
.box {
    /*边框 粗细 样式（实线） 颜色*/
    border: 1px solid red;
    /*边框 粗细 样式（虚线） 颜色*/
    border: 1px dashed red;
}
/*结构伪类选择器*/
div:nth-of-type(1) input {
    border: 1px dashed red;
}
div:nth-of-type(2) input {
    border: 1px dashed red;
}
div:nth-of-type(3) input {
    border: 1px dashed red;
}
```

## 9.2 外边距

```
div {
    /*外边距顺时针，上右下左*/
    margin: 1px 2px 3px 4px;
    margin-top: 1px;
    margin-right: 2px;
    margin-bottom: 3px;
    margin-left: 4px;
}
```

## 9.3 内边距

```
div {
    /*内边距顺时针，上右下左*/
    padding: 1px 2px 3px 4px;
    padding-top: 1px;
    padding-right: 2px;
    padding-bottom: 3px;
    padding-left: 4px;
}
```

## 9.4 盒子的计算方式，你这个元素到底多大

margin + border + padding + 内容的宽度

# 10 圆角边框及阴影

```
div {
    width: 100px;
    height: 100px;
    background: red;
    /*圆角边框 顺时针 左上 右上 右下 左下*/
    border-radius: 50px 0px 50px 0px;
    /*圆圈长度高度的一半是圆的半径和圆角边框像素值一样*/
    border-radius: 50px;
}
```

# 11 display和浮动

## 11.1 display

```
div {
    /*display 属性规定元素应该生成的框的类型*/
    /*块元素*/
    display: block;
    /*行内元素*/
    display: inline;
    /*是块元素，但是可以内联，在一行*/
    display: inline-block;
    /*消失*/
    display: none;
}
```

## 11.2 浮动

```
float: left;
float: right;
```

# 12 overflow及父级边框塌陷问题

## 12.1 clear

```
div {
    float: right;
    /*clear清除浮动 both是两侧都不允许有浮动*/
    clear: left;
    clear: right;
    clear: both;
    clear: none;
}
```

## 12.2 解决方案

1. 增加父元素的高度
2. 在父级标签里面增加一个空的div标签，清除浮动
3. 在父级元素中增加一个overflow: hidden属性
4. 父类添加一个伪类 :after

```
#fater:after {
    content: '';
    display: block;
    clear: both;
}
```

## 12.3 overflow 解决块内容溢出问题

```
div {
    width:150px;
    height:150px;
    overflow:scroll;
  }
```

# 13 定位

## 13.1 相对定位

定位：

相对于自己原来的位置进行定位，它仍然在标准流文档中，原来的位置会被保留

```
div {
    position: relative;
    top: -20px;
    bottom: 10px;
    left: 10px;
    right: 20px;
}
```

## 13.2 绝对定位

定位：

1. 没有父级元素定位的前提下，相对于浏览器定位
2. 父级元素存在相对定位，会对父级元素进行偏移
3. 在父级元素范围内进行偏移

相对于父级或者浏览器的位置，进行指定偏移，绝对定位的话，它不在标准文档中，原来的位置不会被保留

```
#father {
    position: relative;
}
#son {
    position: absolute;
    top: -20px;
    bottom: 10px;
    left: 10px;
    right: 20px;
}
```

## 12.3 固定定位

```css
div {
    position: fixed;
    top: -20px;
    bottom: 10px;
    left: 10px;
    right: 20px;
}
```

# 14 z-index及透明度

```
div {
    /*图层*/
    z-index: 999;
    /*不透明度*/
    opacity: 0.5;
}
```

# 15 动画

了解