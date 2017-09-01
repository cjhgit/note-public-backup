# JavaScript 学习笔记 - 本地存储（LocalStorage）

## 前言

本文主要介绍本地存储的基本使用，以及它和 Cookie、SessionStorage 的区别。

## 简单回顾 Cookie

在 HTML5 之前，本地存储数据一般是通过 Cookie 来完成的。我们可以把 Cookie 理解为一个长度有限的字符串，服务端和客户端都能读写这个字符串，并且每次请求时，都会把 Cookie 发送到服务端。

通常，我们可以利用这个字符串来保存用户名、密码等数据，来实现记住密码、自动登录等功能。

但是，Cookie 本来就不是用来存储数据的，所以会有一些局限性：

* 存储空间有限，最多也就是几十 K 的大小。
* 每次请求都发送到服务器，浪费宽带。
* 使用起来比较麻烦的，需要自己封装操作函数。

## 本地存储的简单使用

本地存储（LocalStorage）是一种基于键值对的持久化存储方案。“持久化存储”就意味着，如果不手动清除，数据就永远不会过期。

基于键值对的存储方案，使用起来是很方便的。我们可以通过 `localStorage.setItem(key, value)` 来保存数据。

比如保存一个用户名：

`javascript-demo/localstorage.html`：

```
localStorage.setItem('name', 'hello')
```

然后就可以通过 `localStorage.getItem(key)` 的方式来获取数据：

```
localStorage.getItem('name') // hello
```

LocalStorage 还支持直接对 `localStorage` 对象的属性进行操作来存取数据，效果和 `setItem`、`getItem` 是一样的。

```
localStorage.hi = 'Hi'
console.log(localStorage.hi) // Hi
```

以上代码等同于：

```
localStorage.setItem('hi', 'Hi')
console.log(localStorage.getItem('hi')) // Hi
```

## 存储对象

本地存储只支持字符串存储，存储任何类型的数据，都会被转换成字符串。

`javascript-demo/localstorage-number.html`：

```
localStorage.setItem('age', 1024)
console.log(typeof localStorage.getItem('age')) // string
```

读取完数据后，还要把数据转成 Number 类型，很麻烦。有时候，我们还需要存储复杂的数据结构。不可能像下面那样将对象的属性一个个存储，再一个个读取。

`javascript-demo/localstorage-object.html`：

```
// 保存对象
let obj = {
    name: 'hello',
    age: 1024
}
localStorage.setItem('name', obj.name)
localStorage.setItem('age', obj.age)
// 读取对象
let newObj = {
    name: localStorage.getItem('name'),
    age: parseInt(localStorage.getItem('age'))
}
console.log(newObj)
```

这时，我们需要利用 JSON API，来简单封装本地存储。原理是保存数据前，通过 `JSON.stringify` 把数据转换成 JSON 字符串再保存；读取数据后，通过 `JSON.parse` 把 JSON 字符串转换成原来的值。

```
// 简单封装
const storage = {
    set: function (key, value) {
        localStorage.setItem(key, JSON.stringify(value))
    },
    get: function (key) {
        return JSON.parse(localStorage.getItem(key))
    }
}
// 保存对象
let obj = {
    name: 'hello',
    age: 1024
}
storage.set('obj', obj)
// 读取对象
console.log(storage.get('obj'))
```

这很方便，存取数字类型时也不需要转换了。

```
storage.set('age', 1024)
console.log(typeof storage.get('age')) // number
```

## API 介绍

一般来说，`setItem` 和 `getItem` 就足够用了。这里大致介绍一下常用的属性和方法，有兴趣的了解一下。

* `localStorage.length`：获得存储的键值对的的个数。
* `localStorage.key(n)`：获得存储的第 n 个元素对的键值（也叫做键名，不要和值搞混了）（下标从 `0` 开始）。
* `localStorage.getItem(key)`：获取 key 对应的 value。
* `localStorage.key`：获取 key 对应的 value，相当于 `getItem`。也可以直接赋值，则相当于 `setItem`。
* `localStorage.setItem(key, value)`：添加键值对到存储。
* `localStorage.removeItem(key)`：移除键值为 key 的键值对。
* `localStorage.clear()`：清除所有数据。

## LocalStorage VS Cookie

在数据存储方面，Cookie 的不足，也就是本地存储的优势，相对于 Cookie，本地存储的优势在于：

* 较大的存储空间。虽然 W3C 对存储空间没有限制，但浏览器有。不同的浏览器的限制大小可能不同。IE8 上是 10MB，Chrome 是 5MB（数据源于网络，本人未去证实）。在未来可能会更大。
* 不用每次请求都发送到服务器，提高请求速度。
* 足够好用的 API 支持，操作简单。

尽管本地存储功能强大，但它和 Cookie 的分工不同，还无法用来取代 Cookie。

一般来说，Cookie 用来与服务器进行交互，而不是用来存储。而 LocalStorage 仅用来存储。 

## 同源限制

LocalStorage 同样受限于同源策略。不同源之间的数据无法共享。关于同源策略，不懂的可以看我的这篇文章：[前端学习笔记 - 跨域](http://www.chenjianhang.com/1992.html)

## Session Storage

SessionStorage 和 LocalStorage 功能类似，区别仅仅是数据保存时间的不同而已。LocalStorage 是持久存储的，如果不手动清除，数据就永远不会失效。而 SessionStorage 的数据存储在窗口对象中，一旦窗口对象没了（用户关闭浏览器或标签页），数据就会丢失。

我们可以简单地测试一下：

`javascript-demo/sessionstorage.html`：

```
console.log(sessionStorage.getItem('name'))
sessionStorage.setItem('name', 'hello')
console.log(sessionStorage.getItem('name'))
```

第一次运行时，控制台输出：

```
null
hello
```

刷新一下浏览器，控制台输出：

```
hello
hello
```

然后打开一个新标签页（不要关闭原来的标签页），在新标签页中打开示例，可以看到控制台输出：

```
null
hello
```

可见，对于不同的标签页，SessionStorage 是无法共享数据的。一旦关闭了标签页或浏览器，存储的数据就再也找不回了。

## 应用

* 比如文章编辑器的实时保存（以及断网时的保存策略）。
* 一些不重要的用户设置。比如某些阅读类的网站，用户可以设置文章的字体大小、配色等。这些数据有时没必要保存在数据库。
* 比如。。。你仔细想想，还是有很多的。

需要注意的是，不要太依赖于本地存储。本地存储虽然是永久的，但随时可能被用户或浏览器清理掉。此外，不同浏览器间也是无法共享数据的。


## 总结

![](http://cdn.chenjianhang.com/javascript-demo/localstorage-mindmap.png)

## 无聊的补充

我们可以这样获取已经占用的存储空间大小：

```
var total = unescape(encodeURIComponent(JSON.stringify(localStorage))).length;
console.log(total / 1024 + 'K')
```

5M 左右的空间，也是会用满的：

```
for (let i = 0; i < 1024 * 1024; i++) {
    localStorage.setItem('test' + i, 'hello')
}
```

控制台输出：

```
Uncaught DOMException: Failed to execute 'setItem' on 'Storage': Setting the value of 'test356613' exceeded the quota.
```

意思是超出配额了。

我们也可以来测试你的浏览器对本地存储的最大允许容量。

```
for (let i = 0; i < 1024 * 1024; i++) {
    var total = unescape(encodeURIComponent(JSON.stringify(localStorage))).length;
    console.log(total / 1024 / 1024 + 'M')

    localStorage.setItem('test' + i, '0')
}
``` 

我试了两个浏览器，360浏览器崩溃了，谷歌浏览器显示 7M 多。