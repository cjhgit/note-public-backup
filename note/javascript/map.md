# Map

## 前言

Map 是常用的数据结构之一，是键值对的集合。关于 Map 的基础知识，这里不再赘述，不懂的自行百度。

## 正文

ES6 出来之前，我们通常用对象来模拟 Map。

`javascript-demo/map-object.html`：

```javascript
let map = {}
map.name = 'example'
map.age = 1024
// 遍历 Map
for (let key in map) {
    console.log(key + ' : ' + map[key])
}
```

输出：

```text
name : example
age : 1024
```

用对象来模拟 Map 有一些局限性，比如 Key 只能是字符串或数字类型。这句话是网上看到的，我没有遇过 key 使用其他类型的情况，也一时想不出使用场景。 

但现在，我们可以使用原生的 `Map` 类型来编程。

我们可以这样修改上面的示例。

`javascript-demo/map-es6.html`：

```javascript
let map = new Map()
map.set('name', 'example')
map.set('age', 1024)
// 遍历 Map
map.forEach(function (value, key) {
    console.log(key + ' : ' + value)
})
```

我觉得这样做的最大好处是：语义化。

Map 相关的语法不多。我们可以通过 `map.set(key, value)` 来保存一对键值对。通过 `map.get(key)` 来获取值。

如果键值对不存在，返回 `undefined`。而不是像 `localStorage.getItem` 那样不存在时返回 `null`（有时候 `undefined` 和 `null` 容易搞混）。

```javascript
// 通过不存在的 key 获取值
console.log(map.get('no-exist')) // undefined
console.log(localStorage.getItem('no-exist')) // null
```

同一个 key 只能对应一个 value，这是 Map 的特性。

```javascript
// 覆盖测试
map.set('test', 'test1')
map.set('test', 'test2')
console.log(map.get('test')) // test2
```

我们可以通过 `map.delete` 删除键值对。

```
// delete 测试
map.set('delete', 'delete')
map.delete('delete')
console.log(map.get('delete')) // undefined
```
