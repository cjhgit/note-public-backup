SVG 学习笔记 - 基本元素.md

## 前言

这是[《SVG 学习笔记》](http://www.chenjianhang.com/1963.html)系列文章之一，点击链接可查看更多 SVG 相关的知识。

这篇文章主要介绍 SVG 的几个基本元素，学完这篇文章，你可以知道如何使用 SVG 绘制基本的几何图形。

## 基本元素

SVG 支持以下几个基本元素：

* 矩形 `<rect>`
* 圆形 `<circle>`
* 椭圆 `<ellipse>`
* 直线 `<line>`
* 折线 `<polyline>`
* 多边形 `<polygon>`
* 文本 `<text>`
* 路径 `<path>`

这几个基本图形组合起来，便可以绘制任何复杂的形状。

### 矩形

将下面代码保存为 `svg` 格式的文件，在浏览器直接打开。

```
<?xml version="1.0" encoding="utf-8"?>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <rect x="16" y="16" width="300" height="100" fill="#42b5f4" />
</svg>
```

效果：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/svg-element-0.png)

属性 | 默认值 | 说明
---|---|---
`x` | `0` | 矩形左上角的 x 坐标
`y` | `0` | 矩形左上角的 y 坐标
`width` | | 矩形的长
`height` | | 矩形的高

### 圆形 circle

```
<?xml version="1.0" encoding="utf-8"?>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <circle cx="100" cy="50" r="40" fill="#db4437"/>
</svg>
```
![](http://www.chenjianhang.com/wp-content/uploads/2017/08/svg-element-1.png)

其中，属性 `cx` 表示圆心的横坐标，`cy` 表示圆心的纵坐标，`r` 表示圆的半径（radius）。

### 椭圆 ellipse

```
<?xml version="1.0" encoding="utf-8"?>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
    <ellipse cx="80" cy="40" rx="80" ry="40" fill="#0f9d58" />
</svg>
```

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/scg-element-2.png)

其中，属性 `cx` 表示椭圆中心的横坐标，`cy` 表示椭圆中心的纵坐标，`rx` 表示椭圆的水平半径， `cy` 表示椭圆的垂直半径。

### 直线 line

```
<?xml version="1.0" encoding="utf-8"?>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
    <line x1="0" y1="0" x2="200" y2="200" stroke="#000" stroke-width="2" />
</svg>
```

效果图：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/svg-element-3.png)

这是一条起始点位于 (x1, y2)，终点位于 (x2, y2) 的直线。

### 多边形 polygon

```
<?xml version="1.0" encoding="utf-8"?>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
    <polygon points="40,0 0,40 80,40" fill="#0f9d58" />
</svg>
```

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/svg-element-4.png)

其中，属性 `points` 表示多边形每一个顶点的坐标。

### 折线 polyline

```
<?xml version="1.0" encoding="utf-8"?>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
    <polyline points="40,0 0,40 80,40" stroke="#000" stroke-width="2" fill="none" />
</svg>
```

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/svg-element-5.png)

其中，属性 `points` 表示折线每一个端点的坐标。

### 文本 text

```
<?xml version="1.0" encoding="utf-8"?>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
    <text x="0" y="16" fill="#db4437">Hello world</text>
</svg>
```

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/svg-element-6.png)

## 路径 path

路径是一个使用起来比较复杂而又功能强大的元素。其实，即使没有其他元素，仅靠 `path` 元素，也可以绘制出任意复杂的形状。

`path` 元素具有以下属性：

* M = moveto（移动到）
* L = lineto（连接直线到）
* H = horizontal lineto（水平连到）
* V = vertical lineto（垂直连到）
* C = curveto
* S = smooth curveto
* Q = quadratic Bézier curve
* T = smooth quadratic Bézier curveto
* A = elliptical Arc
* Z = closepath（关闭路径）

这些属性均允许小写字母，大写表示绝对定位，小写表示相对定位。

```
<?xml version="1.0" encoding="utf-8"?>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <path d="M 100 350 q 150 -300 300 0" stroke="blue" stroke-width="5" fill="none" />
</svg>
```

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/svg-element-7.png)











