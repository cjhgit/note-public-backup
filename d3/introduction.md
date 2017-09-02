# D3.js 学习笔记 - 简介

## 前言

说起数据可视化前端类库，就不得不提起 d3.js。这个 js 库也算是大名鼎鼎了。今天趁着有空，准备深入了解一下。

这是一个系列文章，要求读者具备 HTML、CSS、JavaScript 和 SVG 相关的知识。

如果你阅读起来比较吃力，很可能是你缺少某方面的知识，比如：SVG。你有不懂的地方也可以在文章下面留言，心情好会回复。

除此之外，你还需准备一个较新的浏览器。

## 什么是 d3.js

d3.js，其实就是一个操作 SVG 节点的库，这类库可以让我们像使用 jQuery 操作 DOM 一样操作 SVG 资源。D3.js 和 SVG 的关系，就像 jQuery 和 DOM 的关系一样。

SVG 操作框架，比较出名的有这几个：

* [d3.js](https://d3js.org/)：功能比较强大的 SVG 操作库，经常在数据可视化相关的文章被推荐使用。（[GitHub](https://github.com/d3/d3)，67424 star）
* [Snap.svg](http://snapsvg.io/)：Adobe 出品，功能强大。我关注很久了，但没使用过。（[Github](https://github.com/adobe-webplatform/Snap.svg)，10244 star）
* [SVG.js](http://svgjs.com/)：这是我使用最多的 SVG 操作库，因为她比较小巧。（[Github](https://github.com/svgdotjs/svg.js)，4661 star）

这三者功能很相近，有空我会研究一下 snap.svg，对三者做出横向对比。

所有示例项目引用的是在线 d3.js，如果网络加载慢，你也可以到下面地址下载 d3.js。

* [下载地址 1](https://github.com/d3/d3/releases/download/v4.10.0/d3.zip)