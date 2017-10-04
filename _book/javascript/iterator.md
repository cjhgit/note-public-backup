# Iterator

JavaScript 有几种表示“集合”的数据结构，比如 Array、Object、Map 和 Set，不同的数据类型遍历的方式不同。而很多其他数据类型也有遍历的需求，比如字符串等等。

```javascript
// 遍历数组
let array = [1, 2, 3, 0, 6]
for (let i = 0; i < array.length; i++) {
    console.log(array[i])
}

// 遍历 Set
let set = new Set([1, 2, 3, 0, 6])
set.forEach(function (value) {
    console.log(value)
})

// 遍历字符串
let string = 'hello'
for (let i = 0; i < string.length; i++) {
    console.log(string.charAt(i))
}
```

迭代器（Iterator）有时也叫做遍历器，是一种接口，不同的数据类型只要实现了这个接口，就可以使用统一的遍历方式。如果你学过 Java 或 C++，想必对迭代器这个概念不会陌生。

但是，JavaScript 是不支持接口的。ES6 规定，一个数据类型如果具有 `Symbol.iterator` 属性，就相当于“实现了 `Iterator` 接口”。

JavaScript 原生实现了这个接口的数据类型有：

* String
* Array
* TypedArray
* Map
* Set
* arguments
* NodeList

我们来看看，用迭代器是怎么实现遍历数组的。

```javascript
let array = [1, 2, 3]
let iterator = array[Symbol.iterator]()
console.log(iterator.next()) // Object {value: 1, done: false}
console.log(iterator.next()) // Object {value: 2, done: false}
console.log(iterator.next()) // Object {value: 3, done: false}
console.log(iterator.next()) // Object {value: undefined, done: true}
```

和上面的示例一样，迭代器的使用套路一般是：

1. 调用实现了迭代器接口的数据类型的对象的 `Symbol.iterator` 方法，获取迭代器 `iterator`。
2. 通过 `iterator.next()` 获取下一个数据（value）以及是否遍历完成的标记（done）。

我们可以用 `while` 循环来遍历数据。

```javascript
let array = [1, 2, 3]
let iterator = array[Symbol.iterator]()
let ret = iterator.next()
while (!ret.done) {
    console.log(ret.value)
    ret = iterator.next()
}
```

所有实现了`Iterator` 接口的数据类型，都可以采用这种统一的方式来遍历数据。

虽然形式是统一了，但相对于 `for` 循环这种遍历，这样实现的代码显然不够简洁。为此，ES6 提供了 `for...of` 循环，只要是实现了 `Iterator` 接口的数据类型，都可以使用 `for...of` 循环来遍历。

对于本文第一个示例，现在我们可以这样实现：

```javascript
// 遍历数组
let array = [1, 2, 3, 0, 6]
for (let value of array) {
    console.log(value)
}

// 遍历 Set
let set = new Set([1, 2, 3, 0, 6])
for (let value of set) {
    console.log(value)
}

// 遍历字符串
let string = 'hello'
for (let value of string) {
    console.log(value)
}
```

实际上，`for...in` 循环内部也是调用 Iterator 接口实现的。

// TODO 未完待续
