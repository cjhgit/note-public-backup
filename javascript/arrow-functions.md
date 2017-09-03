# 箭头函数

## 前言

本文介绍箭头函数相关的基础概念和语法。

## 基础知识

箭头函数（Arrow functions）是 ES6 的一个新特性。使用它有两个好处：更简洁的语法和共享 `this` 上下文。

### 简洁的语法

对于函数的定义，我们一般是这么写的：

```
function(parameters) {
	statements
}
```

如果使用箭头函数的语法，可以这样成：

```
(parameters) => { statements }
```

如果没有参数，可以这样写（括号不能省略）：

```
() => { statements }
```

如果只有一个参数，可以这样写：

```
parameters => { statements }
```

如果有返回值，并且只有一个表达式，可以省略大括号和 `return`：

```
parameters => expression
```

举个栗子：

`javascript-dmeo/arrow-functions.html`：

```
function add(a, b) {
    return a + b
}

console.log(add(1, 2)) // 3
```

这里定义了一个加法计算的函数。如果用 ES6，可以这么写：

`javascript-dmeo/arrow-functions-1.html`：

```
let add = (a, b) => a + b

console.log(add(1, 2)) // 3
```

### 共享 `this` 上下文

## 总结