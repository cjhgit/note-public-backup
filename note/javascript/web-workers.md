# Web Workers

## 前言

本文仅是 Web Workers 的入门科普文章，不涉及太琐碎的知识点。

我们知道，在 Web Workers 出来之前，JavaScript 是单线程的。即使是 `setTimeout` 之类的看似多线程的函数，实际上也是单线程执行的。

有时，我们需要在浏览器执行一个比较耗时的计算：

```
function count() {
    let i = 0
    let sum = 0

    for (let j = 0; j < 100; j++) {
        for (let i = 0; i < 100000000; i++) {
            sum += i
        }
    }

    return sum
}
```

如果直接在浏览器执行这段代码，会把浏览器卡死。对于这类耗时的计算，可以通过多线程来解决。

多线程的重要性不言而喻。而工作线程（Web Workers），就是 JavaScript 的多线程解决方案。

## 创建工作线程

创建工作线程很简单，只要新建一个 `Worker` 对象就可以了。

`css-demo/web-worker.html`：

```
let worker = new Worker('worker.js')
```

这段代码创建了一个工作线程，用来执行 `worker.js` 的代码。我们可以在 `worker.js` 执行比较耗时的计算。

我们可以写一个简单的工作线程代码：

`css-dmeo/worker.js`：

```
console.log('hello world')
```

运行 `css-demo/web-worker.html`，可以看到控制台输出：

```
Failed to construct 'Worker': Script at 'file://xxx/javascript-demo/worker.js' cannot be accessed from origin 'null'
```

这是因为跨域的原因，导致代码执行失败。我们可以创建一个服务器环境（推荐 Http-server）来打开 HTML。

可以看到控制台输出：

```
hello world。
```

## 线程间消息传递

通常我们在工作线程完成计算后，需要将计算结果传回给主线程。我们可以通过 `postMessage` 方法把数据传给主线程。

`web-worker-message.js`：

```
postMessage('hello world')
```

主线程注册 `onmessage` 回调函数，通过 `event.data` 接收工作线程传递过来的数据。

`web-worker-message.html`：

```
let worker = new Worker('web-worker-message.js')
// 设置回调函数，接收 worker 传递过来的数据
worker.onmessage = function(event) {
    console.log(event.data)
}
```

执行后，控制台输出：

```
hello world
```

当然，我们也可以传递其他类型的数据。比如，要传递多个数据时，可以先构造个对象，再传递过去。

```
postMessage({
    data1: 'hello',
    data2: 'world'
})
```

## API 介绍

![](http://cdn.chenjianhang.com/javascript-demo/web-worker/worker-worker.png)

### postMessage

`postMessage(data, origin)`：工作线程向主线程传递数据，`data` 是传递的数据，`origin` 用来设置跨域相关的东西，这里不做介绍。

### terminate

`terminate()` 函数用来结束工作线程。

`web-worker-terminate.html`：

```
let worker = new Worker('web-worker-terminate.js')
worker.terminate()
```

`web-worker-terminate.js`：

```
setTimeout(function () {
    console.log('hello')
}, 1000)
```

运行后，等了会儿，和预期的一样，控制台没有任何输出。

### onmessage

`onmessage`：用来接收工作线程传递给主线程的消息。

### onerror

`onerror` 用来处理线程错误。

`web-worker-onerror.html`：

```
let worker = new Worker('web-worker-onerror.js')
worker.onerror = function(e) {
    // 打印错误消息
    console.log(e.message)
}
```

`web-worker-onerror.js`：

```
undefinedFunction()
```

控制台输出：

```
Uncaught ReferenceError: undefinedFunction is not defined
```

除了普通的异常错误，404 等 HTTP 请求错误时也能回调。

```
let worker = new Worker('no-exist-url.js')
worker.onerror = function(e) {
    // 打印错误消息
    console.log(e.message)
}
```

控制台输出：

```
undefined
```

## 工作线程上下文

如果你试过在工作线程中执行 `alert` 函数，就会执行出错。

```
Uncaught ReferenceError: alert is not defined
```

这是因为在工作线程中，JavaScript 代码执行的上下文（Runtime Context）并不是 Window 对象。

你可以在工作线程中执行：`console.log(Window)`，控制台会输出：

```
Uncaught ReferenceError: Window is not defined
```

我们可以通过 `console.log(this)` 把工作线程中当前上下文对象打印出来。

![](http://cdn.chenjianhang.com/javascript-demo/web-worker/web-worker-this.png)

输出的不是 `Window` 对象。由于上下文的不同，工作线程的 JavaScript API 会和以前的用法有点不一样。最大的区别在于：工作线程中不能操作 DOM。

工作线程的职责在于处理数据，然后把处理完成的数据传给主线程，主线程再根据数据更新界面。 

可能有人觉得这样很麻烦，如果你做过多线程界面开发（比如 Android），应该清楚这样做的原因：在多个线程同时更新 UI 的很不安全的。

## 总结

知识点不多，对于一般的使用，应该足够了。

![](http://cdn.chenjianhang.com/javascript-demo/web-worker/web-workers-mindmap.png)

