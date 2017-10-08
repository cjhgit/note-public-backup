# 选择器

在 CSS 中，规则由选择器（Selectors）和声明块组成，声明块确定了元素的样式，选择器确定了样式作用于哪些元素。

通常，将选择器分成以下类别：

* 简单选择器（Simple selectors）：根据元素类型、class 或 id 匹配元素。
* 属性选择器（Attribute selectors）：根据属性或属性值匹配元素。
* 伪类（Pseudo-classes）：根据状态匹配元素。
* 伪元素（Pseudo-elements）：根据元素位置匹配元素。

## 简单选择器

### 类型选择器（元素选择器）

### 属性选择器

示例 | 说明
--- | ---
[attr] | 匹配具有 `attr` 属性的元素
[attr=value] | 匹配具有 `attr` 属性并且属性值为 value 的元素

## 伪类

示例 | 说明
--- | ---
a:link | 未访问的链接
a:visited | 访问过的链接
a:hover | 鼠标悬浮时的链接
a:active | 处于 active 状态的链接
:first - child

## 伪元素

示例 | 说明
--- | ---
:first-line | 文本的首行
:first-letter | 文本的首字母
:before | 在元素的内容前面插入新内容
:after | 在元素的内容后面插入新内容





:lang