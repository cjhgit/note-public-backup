# 算法

算法（Algorithm）

* 时间复杂度
* 空间复杂度




## 排序算法

### 冒泡排序（Bubble Sort）





## 算法题

回文（字符串倒置）：

```javascript
function f(str) {
    return str.split('').reverse().join('')
}
console.log(f('hello world')) // dlrow olleh
```

数组去重：

```javascript
function f(arr) {
    let newArr = []
    let set = new Set()
    arr.forEach(item => {
        if (!set.has(item)) {
            newArr.push(item)
            set.add(item)
        }
    })
    return newArr
}
console.log(f([1, 2, 3, 3, 4, 1, 5])) // [1, 2, 3, 4, 5]
```

精简版：

```javascript
function f(arr) {
    return Array.form(new Set(arr)) // TODO 待测试
}
console.log(f([1, 2, 3, 3, 4, 1, 5]))
```

统计字符串中出现最多的字符：

```javascript
function f(str) {
    let map = new Map()
    let char = ''
    let maxCount = 0
    for (item of str) {
        if (map.get(item)) {
            let count = map.get(item) + 1
            map.set(item, count)
            if (count > maxCount) {
                maxCount = count
                char = item
            }
        } else {
            map.set(item, 1)
        }
    }
    return char
}
console.log(f('122333444455555')) // 5
```


TODO

* 算法导论