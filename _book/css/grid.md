# CSS 学习笔记 - Grid 布局

## 前言

网格布局（Grid Layout）是 CSS3 的一种新的布局方式。

## 基本概念

我们可以设置 `display: grid` 或 `display: inline-grid` 来使用网格布局。

```
.container {
    display: grid;
}
```

学习之前，先来学习一些基本的定义。

我们把设置了 `display: grid` 的元素叫做网格容器（Grid Container），其子元素叫做网格项（Grid Item）。

网格线（Grid Lines）顾名思义，就是网格中把界面分成若干块的分割线。

网格轨道（Grid Track）就是类似表格中的行或者列的概念。

![](http://cdn.chenjianhang.com/css-demo/grid/grid-track.png)

网格单元（Grid Cell）就是类似表格中的单元格的概念。

![](http://cdn.chenjianhang.com/css-demo/grid/grid-cell.png)

网格区域（Grid Area）就是任意四条网格线围成的区域。

![](http://cdn.chenjianhang.com/css-demo/grid/grid-area.png)

## 属性介绍

网格容器支持以下属性：

* grid-template-rows
* grid-template-areas
* grid-column-gap
* grid-row-gap
* grid-gap
* justify-items
* align-items
* justify-content
* align-content
* grid-auto-columns
* grid-auto-rows
* grid-auto-flow
* grid

网格项支持以下属性：

grid-column-start
grid-column-end
grid-row-start
grid-row-end
grid-column
grid-row
grid-area
justify-self
align-self

如果你学过 Flex 布局，可以发现某些属性和 Flex 是相似的。毕竟很多东西，原理都是相通的。

我数了一下，一共 22 个属性。再加上每个属性的值和配图，这会是一片很长的文章。

为了防止文章过长，这里只介绍部分属性。

### grid-template-rows 和 grid-template-columns

`grid-template-rows` 和 `grid-template-columns` 分别用来设置网格项每一行和每一列的大小。

一个简单是示例：

```
grid-template-columns: 40px 80px 40px 40px;
grid-template-rows: 40px 80px 40px;
```

效果：

![](http://cdn.chenjianhang.com/css-demo/grid/grid-0.png)

### grid-gap

`grid-gap` 是 `grid-column-gap` 和 `grid-row-gap` 的缩写。如果写一个值，表示 `grid-column-gap` 和 `grid-row-gap` 都设置成那个值。

```
grid-gap: <grid-column-gap> <grid-row-gap>;
```


### justify-content

`justify-content` 属性用来设置网格项的水平对齐方式。它有以下五个值。

`start`（默认值）: 左对齐。

![](http://cdn.chenjianhang.com/css-demo/grid/justify-content-start.png)

`end`: 右对齐。

![](http://cdn.chenjianhang.com/css-demo/grid/justify-content-end.png)

`center`: 居中对齐。

![](http://cdn.chenjianhang.com/css-demo/grid/justify-content-center.png)

`stretch`: 占满网格容器宽度。

![](http://cdn.chenjianhang.com/css-demo/grid/justify-content-stretch.png)

该属性会被 `grid-template-colnums` 属性影响。如果在 `grid-template-colnums` 设置了某一列的宽度，这个属性不会对该列的宽度起作用。

// TODO 具体如何影响，有空再补充。

`space-around`: 网格项两边间距相等。网格项之间的间距是边上的间距的的两倍。

![](http://cdn.chenjianhang.com/css-demo/grid/justify-content-space-around.png)

`space-between`: 两端对齐。网格项之间的间距相等。

![](http://cdn.chenjianhang.com/css-demo/grid/justify-content-space-between.png)

space-evenly: 网格项间距相等。

![](http://cdn.chenjianhang.com/css-demo/grid/justify-content-space-between.png)

### align-content

`align-content` 属性用来设置网格项在垂直方向的对齐方式。它有以下七个属性。

`start`: 顶部对齐（默认）。

![](http://cdn.chenjianhang.com/css-demo/grid/align-content-start.png)

`end`: 底部对齐。

![](http://cdn.chenjianhang.com/css-demo/grid/align-content-end.png)

`center`: 垂直居中对齐。

![](http://cdn.chenjianhang.com/css-demo/grid/align-content-center.png)

`stretch`: 占满网格容器高度。

![](http://cdn.chenjianhang.com/css-demo/grid/align-content-stretch.png)

`space-around`: 网格项两边间距相等。

![](http://cdn.chenjianhang.com/css-demo/grid/align-content-space-around.png)

`space-between`: 两端对齐。

![](http://cdn.chenjianhang.com/css-demo/grid/align-content-space-between.png)

`space-evenly`: 网格项间距相等。

![](http://cdn.chenjianhang.com/css-demo/grid/align-content-space-evenly.png)

// TODO 未完待续
