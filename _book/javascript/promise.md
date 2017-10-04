# Promise

## 回调函数的弊端

对于一些常见的耗时操作，比如 AJAX，一般是通过回调函数来实现异步编程的。

```
ajax(url, function () {
	// 这里执行请求完成后的操作
})
```

回调函数的弊端在于：多层调用时，可读性很差。

比如有三个 AJAX 请求，必须顺序执行。

```
ajax(url, function () {
	ajax(url2, function () {
		ajax(url3, function () {
	
		})
	})
})
```

Promise 能解决这个问题，实现更优雅的异步代码。

## Promises 基本概念

Promises 是一个异步编程的规范，这个规范规定了一些异步编程基本的概念、语法和一些必须遵守的规则，但没有给出具体的实现。这个规范最新的版本是 Promises/A+。我们可以在[官网](https://promisesaplus.com/)查看关于这个规范相关的说明。

Promises 的实现有很多现成的第三方库，而 ES6 的 Promises 是 Promises/A+ 提案的一种实现。

介绍概念之前，我们可以先执行下面这段代码。对 Promise 有个初步的印象

```
var promise = new Promise(function(resolve, reject) {
    setTimeout(function() {
        resolve()
    }, 1000)
})

promise.then(function(value) {
    console.log('success')
}, function(value) {
    console.log('failure')
})
```

在控制台可以看到，一秒后，控制台输出：success。

所谓 Promise，就是一个对象，其构造函数有两个参数：`resolve` 和 `reject`。

Promise 对象有以下三个状态：

* pending：初始状态，等待中，表示异步操作还没有结果。
* resolved：完成，表示异步操作成功。
* rejected：拒绝，表示异步操作失败。

要想改变状态，只能通过构造函数的两个参数来改变。`resolve` 函数把状态从 pending 改变为 resolved；`reject` 函数把状态从 pending 改为 rejected。并且，一旦修改，状态就无法再改变。也就是说，Promise 的状态是单向不可逆的。正如它的名字“承诺”一样，一旦承诺，便不再反悔。

![](http://cdn.chenjianhang.com/javascript-demo/promise-state.png)


看到这里，我想你应该知道 Promise 构造函数的作用了：执行异步操作代码，并根据结果调用 `resolve` 或 `reject` 改变 Promise 的状态。

这是 Promise 的使用套路：

```
var promise = new Promise(function(resolve, reject) {
    执行异步操作
    if (操作成功) {
        resolve()
    } else {
        reject()
    }
}).then(function(value) {
    操作成功回调
}, function(value) {
    操作失败回调
})
```

`then` 函数有两个参数，分别是执行成功时的回调函数和执行失败时的回调函数。当 Promise 的状态改变时，Promise 对象会自动调用回调函数。

我们也可以调用多次 `then` 函数，来实现多个回调。

`javascript-demo/promise-3.html`：

```
var promise = new Promise(function(resolve, reject) {
    resolve()
}).then(function(){
    console.log('完成回调1')
}).then(function(){
    console.log('完成回调2')
})
```

控制台输出：

```
完成回调1
完成回调2
```

// TODO 未完待续

## 参考

* [Promise - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
* [Promises/A+](https://promisesaplus.com/)