# Canvas 学习笔记 - 简介

## 前言

Canvas，有时也称作画布，是 HTML5 新增的一个元素。通过 JavaScript Canvas API，我们可以在画布上绘制任何图形、动画。

在 Canvas 诞生之前，网页绘图只能通过 Flash 实现，需要 JavaScript 与 Flash 交互，学习成本很高。而 Canvas 的诞生，宣告了 Flash 时代的终结。

Canvas 是 HTML5 最强大的功能之一。如果你想学习高级一点的网页动画效果，或者做个网页小游戏，学习 Canvas 是必不可少的。此外，由于 Canvas 是基于像素操作的，利用 Canvas 提供的像素操作 API，还可以实现图像处理等功能。总而言之，Canvas 赋予了网页无限的可能。

这篇文章，主要介绍如何通过 Canvas 绘制基本的几何图形。

## Canvas 坐标系

在绘制前，我们先来学习 Canvas 的坐标系。

![Canvas 的坐标系统](http://www.chenjianhang.com/wp-content/uploads/2017/08/canvas-hello-coord.png)

和绝大多编程语言的图形库一样，Canvas 的坐标系统也是以左上角为原点，水平向右方向为 x 轴方向，垂直向下方向为 y 轴方向，以像素为单位长度。

如果你有学过其他编程语言的图形库（如 Android 等）或者 SVG，你会发现很多功能是相似的，比如坐标系的概念、画布的概念、贝赛尔曲线，等等。


## 绘制基本图形

### 直线

`canvas-demo/line.html`：

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
</head>
<body>

<canvas id="canvas" width="320" height="160" style="border:1px solid #999;"></canvas>

<script>
	var canvas = document.getElementById('canvas')
	var ctx = canvas.getContext('2d')
	ctx.beginPath()
	ctx.moveTo(80, 80)
	ctx.lineTo(240, 80)
	ctx.stroke()
</script>

</body>
</html>
```

运行效果：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/canvas-hello-line.png)

示例中，创建了一个 `canvas` 元素，并设置画布宽和高。

我们在使用画布绘制图形时，一般都是以下几个步骤：

1. 获取 `canvas` 对象。
2. 获取 Canvas 的上下文（Context）：`canvas.getContext('2d')`。参数只能写 `2d`。
3. 开始新的路径：`ctx.beginPath()`。这一步告诉浏览器，我要开始绘图了。
4. 绘图。
5. 填充（fill）或描边（stroke）。线只支持描边，不支持填充。非线图形既可以填充，也可以描边。

其中，`moveTo` 表示“画笔”移动到某个点（并没有连线），`lineTo` 表示“画笔”从当前位置直线连到某个点。

我们也可以通过这两个 API 来绘制折线。

## 折线

`canvas-demo/polyline.html`（只展示关键源码，下同）：

```
ctx.beginPath()
ctx.moveTo(80, 80)
ctx.lineTo(160, 40)
ctx.lineTo(240, 80)
ctx.stroke()
```

效果：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/canvas-hello-polyline.png)

## 矩形

`canvas-demo/rect.html`：

```
ctx.rect(40, 40, 240, 80)
ctx.stroke()
```

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/canvas-hello-rect.png)

其中，四个参数分别为矩形的左上角 x 坐标、左上角 y 坐标、长、宽（高）。

## 弧线



语法如下：

```
context.arc(x, y, r, sAngle, eAngle, counterclockwise)
```

参数 | 说明
--- | ---
x | 圆心的 x 坐标
y | 圆心的 y 坐标
sAngle | 起始角度（单位弧度）
eAngle | 结束角度（单位弧度）
counterclockwise | 是否逆时针绘图。可选。默认值是 false，即顺时针绘图。

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/canvas-hello-arc-2.png)

`canvas-demo/arc.html`：

```
ctx.beginPath()
ctx.arc(160, 80, 40, 0.25 * Math.PI, 1.75 * Math.PI)
ctx.stroke()
```

效果：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/canvas-hello-arc.png)

如果逆时针绘制弧形：

`canvas-demo/arc-counterclockwise.html`：

```
ctx.beginPath()
ctx.arc(160, 80, 40, 0.25 * Math.PI, 1.75 * Math.PI, true)
ctx.stroke()
```

效果：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/canvas-arc-counterclockwise.png)

## 圆形

Canvas 没有提供画圆形的 API，但提供了绘制弧线的 API。

`canvas-demo/circle.html`：

```
ctx.beginPath()
ctx.arc(160, 80, 40, 0, 2 * Math.PI)
ctx.stroke()
```

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/canvas-hello-circle.png)

## 文本

```
ctx.font = '32px Arial'
ctx.fillText('Hello world', 0, 32)
```

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/canvas-hello-font.png)


粒子
http://www.cnblogs.com/axes/p/3606566.html
