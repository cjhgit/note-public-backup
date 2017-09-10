# 数组

## 什么是数组

在编程语言中，数组是最常见的数据类型之一，用来表示数据的集合（跟数学上的集合不一致，一个数组中允许多个相同的值存在）。

我们通常用方括号 `[]` 表示集合，数据之间用英文逗号分隔。

```javascript
['张三', '李四', '王五']
```

在静态编程语言中，数组表示具有相同类型的变量的集合，而在 JavaScript 等动态编程语言中，允许数组中存在多种不同类型的值。

```javascript
let array = ['字符串', 1024, {}, [], 1.01, new Date()]
```
有了数组，借助循环语句，我们便可以对数据进行批量操作。

我们可以用 `arr.length` 来获取数组的长度，通过下标来访问数组中的数据。

```javascript
let arr = ['张三', '李四', '王五']
console.log(arr.length) // 3
console.log(arr[0]) // 张三
```

// TODO 

### map 方法

```javascript
let arr = [1, 4, 9, 16, 25]
console.log(arr.map(Math.sqrt)) // [1, 2, 3, 4, 5]
```

### filter

```javascript
let arr = [1, 4, 9, 16, 25]
function filter(num) {
    return num < 10
}
console.log(arr.filter(filter)) // [1, 4, 9]
```

### reduce

```javascript
let arr = [1, 2, 3, 4]
function sum(total, value) {
    return total + value
}
console.log(arr.reduce(sum)) // 10
```

```javascript
// 计算 1^2 + 2^2 + 3^2
console.log([1, 2, 3].reduce((total, value) => total + value * value)) // 14
```

### some

判断数组中是否含有大于 5 的数

```javascript
let arr = [1, 4, 9, 16, 25]
function check(value) {
    return value > 5
}
console.log(arr.some(check)) // true
```

### includes

`Array.prototype.includes` 是 ES7 新增的一个数组方法，用来判断数组是否包含某个值。

```javascript
let arr = [1, 4, 9, 16, 25]
console.log(arr.includes(4)) // true
console.log(arr.includes(3)) // false
```
