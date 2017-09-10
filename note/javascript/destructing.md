# 解构

### 什么是解构

解构（Destructuring）是 ES6 新增的一种便捷的赋值语法。等号左右两边的形式相同（两边都是数组或都是对象）时，可以进行快速赋值。

### 数组的解构赋值

当等号两边都是数组时，会根据下标的位置对等号左边的数组的元素一一赋值。

```javascript
let a, b, c
[a, b, c] = [1, 2, 3]
console.log(a, b, c) // 1 2 3
```

也可以简写成：

```javascript
let [a, b, c] = [1, 2, 3]
console.log(a, b, c) // 1 2 3
```

`赋值失败时，属性值为 `undefined`。

```javascript
let [a, b, c] = [1, 2]
console.log(a, b, c) // 1 2 undefined
```

等号两边的形式未必要完全一致：

```javascript
let [a, b] = [1, 2, 3]
console.log(a, b) // 1 2
```

支持嵌套：

```javascript
let [a, [b, c]] = [1, [2, 3]]
console.log(a, b, c) // 1 2 3
```

还可以设置默认值：

```javascript
let [a = 1, b = 2] = []
console.log(a, b) // 1 2
```

### 对象的解构赋值

对象的解构语法和数组类似。

```javascript
let {a, b} = {
    a: 1,
    b: 2
}
console.log(a, b) // 1 2
```

### 参数的解构赋值

