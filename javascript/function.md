# 函数

## 尾逗号

ES6 允许函数添加尾逗号（trailing comma），即在最后一个参数后面加逗号。

```javascript
function f(a, b,) {
  
}
```

## 剩余参数

剩余参数（rest parameter）允许我们在参数列表中用一个数组变量表示“剩下的参数”。

在开发中，经常遇到不定数量的参数的场景。比如加法计算函数，我们希望是这样使用的：

```
add(1, 2) // 3
add(1, 2, 3) // 6
```

在 ES6 发布之前，我们一般用 `arguments` 来获取不定参数。

```javascript
function add(...rest) {
    let total = 0
    for (let i = 0; i < arguments.length; i++) {
        total += arguments[i]
    }
    return total
}

console.log(add(1, 2)) // 3
console.log(add(1, 2, 3)) // 6
```

现在，我们多了一种选择，可以用剩余参数实现。

```javascript
function add(...rest) {
    let total = 0
    for (let value of rest) {
        total += value
    }
    return total
}

console.log(add(1, 2)) // 3
console.log(add(1, 2, 3)) // 6
```

剩余参数必须放在参数列表的最后一个，表示“剩下的参数”。

```javascript
function f(a, b, ...rest) {
    console.log(rest.length) 
}

f(1, 2, 3, 4, 5) // 1 2 [3, 4, 5]
```

我们知道，`arguments` 只是一个“类数组”，并不是一个真正的数组，而剩余参数是真正的数组对象，它拥有数组的一切属性和方法。

比如获取数组的长度（剩余参数的数量）：

```javascript
function f(a, b, ...rest) {
    console.log(rest.length)
}

f(1, 2, 3, 4, 5) // 3
```
