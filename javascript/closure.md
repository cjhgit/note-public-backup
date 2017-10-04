# 闭包

## 前言

本文主要介绍我对闭包的理解，要求读者了解 JavaScript 的作用域。

闭包（Closure）是编程中常见的一个概念，这个概念并不是 JavaScript 独有的。记得当初面试我现在工作的这家公司时，就被问到了闭包是什么，当时竟一时不知道怎么回答，便强扯道：“我知道闭包是什么，但我不知道怎么表达。”看那面试官的眼神，明显是不相信我的鬼话。好在他也没有在这问题上深究。

## 什么是闭包

要理解闭包的概念，首先需要知道 JavaScript 的作用域（Scope）。

JavaScript 的作用域有两种：全局作用域和函数作用域。

我们知道，函数内可以访问全局变量（global），但函数外无法直接访问函数内定义的局部变量（local）。

`javascript-demo/closure-0.html`：

```
let global = 1024
function test() {
    let local = 2048
    console.log(global)
}
test()
console.log(local)
```

控制台输出：

```
1024
Uncaught ReferenceError: local is not defined
```

全局变量和局部变量除了作用域不同外，生命周期也是不同的。全部变量在页面关闭才会被销毁，而局部变量在函数执行完毕后就会被销毁。

在上例中，`test` 函数执行完，`local` 变量就会被销毁。

一般来说，函数外是无法直接访问函数内定义的变量的，但我们可以通过间接的形式。

`javascript-demo/closure-1.html`：

```
function test() {
    let local = 2048

    function log() {
        console.log(local)
    }

    return log
}

let test2 = test()
test2() // 2048
```

很显然，`log` 函数是能够访问到 `local` 变量的。`test` 函数返回 `log` 函数，并赋值给 `test2` 变量保存起来，所以在 `tets` 函数外我们可以访问 `log` 函数。这样，就实现了在函数外访问到函数内的变量了。

而示例中的 `log` 函数，就是闭包。说白了，闭包就是一个函数（所以有时也称闭包为闭包函数），这个函数（`log`）有权访问另一个函数（`test`）的内部变量（`local`）。

## 闭包与垃圾回收机制

如果你仔细思考，你就会发现。既然函数外能够访问到 `local` 变量，那么 `local` 变量肯定还在内存中，并没有被销毁。

这是因为 `local` 变量被 `log` 函数引用，`log` 函数被全局变量 `test2` 引用，导致了 `local` 变量无法被垃圾回收机制回收。

所以，滥用闭包，容易浪费内存。

## 总结

略。

![](http://cdn.chenjianhang.com/javascript-demo/closure-mindmap.png)
