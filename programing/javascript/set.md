# Set

## 前言

Set 也叫做集合，是常用的数据结构之一，表示不包含重复项的数据集合。

## 正文

我们可以通过 `new Set()` 新建一个 Set 对象，也可以在构造函数中使用数组作为参数，用来初始化。

`Set` 是属性和方法：

属性或方法 | 说明
--- | ---
add(value) | 添加一个值。返回 Set 本身，便于链式操作。
delete(value) | 删除一个值，返回一个布尔值，表示是否删除成功。
has(value) | 返回一个布尔值，表示是否包含某个值。
clear() | 清除集合。没有返回值。