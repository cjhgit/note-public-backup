# 指数操作符

指数操作符（Exponentiation Operator）是 ES 2016（ES 7） 的新特性之一，用来表示指数运算。

比如要表示 2 的 3次方，我们可以这样写：

```javascript
2 ** 3
```

这相当于：

```javascript
Math.pow(2, 3)
```

示例：

```javascript
console.log(Math.pow(2, 3)) // 8
console.log(2 ** 3) // 8
let num = 2
num **= 3
console.log(num) // 8
```
