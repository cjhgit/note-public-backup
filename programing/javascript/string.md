# 字符串

[JavaScript](/javascript.html)

## 前言

略。

## 正文


### String padding

ES8 新增了 `String.prototype.padStart` 和 `String.prototype.padEnd` 两个方法，用于在字符串开头或结尾处填充字符串。

```javascript
String.prototype.padStart(maxLength [ , fillString ] )
String.prototype.padEnd( maxLength [ , fillString ] )
```

第一个参数表示目标长度，当字符串的长度小于目标长度时，会填充字符使字符串的长度等于目标长度。

```javascript
'es8'.padStart(2);          // 'es8'
'es8'.padStart(5);          // '  es8'
'es8'.padStart(6, 'woof');  // 'wooes8'
'es8'.padStart(14, 'wow');  // 'wowwowwowwoes8'
'es8'.padStart(7, '0');     // '0000es8'

'es8'.padEnd(2);          // 'es8'
'es8'.padEnd(5);          // 'es8  '
'es8'.padEnd(6, 'woof');  // 'es8woo'
'es8'.padEnd(14, 'wow');  // 'es8wowwowwowwo'
'es8'.padEnd(7, '6');     // 'es86666'
```

示例：

```javascript
let minute = 5
let second = 8
let time = ('' + minute).padStart(2, '0') + ':' + ('' + second).padStart(2, '0')
console.log(time) // 05:08
```

字符串填充（String padding）还经常用于格式化输出信息，比如格式化命令行，让输出的信息对齐。


