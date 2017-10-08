# XML

XML （Extensible Markup Language）指可扩展标记语言。

## 组成

```xml
<?xml version="1.0" encoding="UTF-8"?>
<student>
	<name>张三</name>
	<age>18</age>
</student>
```
XML 文档的第一行通常是一个 XML 声明，这个声明告诉人们或机器，这是一个 XML 文件。你可以将这个声明简写成 `<?xml?>`，也可以给它加上属性 `version`，标识这个 XML 的版本号，加上属性 `encoding` 标注这个文档的编码类型。

## 元素（elements）

XML 元素指的是从（且包括）开始标签直到（且包括）结束标签的部分。
在上面的 XML 示例中，一共有三个元素：student、name、age。student 是根元素，name 和 age 是 student 的子元素。

在上面的 XML 示例中，name 元素 由开始标签 `<name>` 和结束标签 `</name>` 已经之间的内容“张三”组成。

### 根元素

一个 XML 文档只有一个根元素。

### 元素命名

元素的命名规则如下：

* 名称可以包含字母、数字以及其他的字符。
* 名称不能以数字或者标点符号开始。
* 名称不能以字母 xml（或者 XML、Xml 等等）开始。
* 名称不能包含空格。

```
// 下面的命名是正确的
<myname></myname>
<my-name></my-name>
<myName></myName>

// 下面的命名是错误的
<my name></my nmae>
<xml-node></xml-node>
```

## 属性

在 XML 中，属性用来为元素提供额外的信息，先看一个 XML 片段：

```
<image src="computer.gif">
<link href="demo.html">
```

在实例中，`image` 元素有一个属性 `src`，这个属性的值为 computer.gif；link 元素有一个属性 href，它的值为 demo.html。

## 语法规则

* 所有的 XML 标签都必须有关闭标签。
* XML 标签对大小写敏感。
* XML 标签必须正确地嵌套。

## 结尾

这篇文章只是简单地介绍 XML 相关的入门知识。