# JSON 学习笔记

## JSON 是什么？

JSON（JavaScript Object Notation）是一种轻量级的数据交换格式，易于阅读和编写，同时也易于机器解析和生成。它基于 ECMAScript 的一个子集。 

## 语法规则

* 数据在键值对中。
* 数据由逗号分隔。
* 花括号保存对象。
* 方括号保存数组。

JSON 名/值对的格式是：

```
"字段名称": 值
```

JSON 的值可以是以下几种类型：

* 数字（整数和浮点数）
* 字符串（在双引号中）
* 逻辑值（true 或 false）
* 数组（在方括号中）
* 对象（在花括号中）
* null

下面是一个简单的 JSON 示例，方便我们理解上述的规则：

```json
{
	"name": "张三",
	"age": 18,
	"address": {
	     "province": "广东省",
	     "city": "广州市",
         "street": "新港中路XX号"
     },
     "phoneNumber": [
         {
	           "type": "phone",
	           "number": "020 1234567"
         },
         {
	           "type": "telphone",
	           "number": "15602221234"
         }
     ]
}
```

## JSON 与 XML 比较

JSON 和 XML 是两种不同的数据格式，各有优缺点。由于它们常用于数据储存和交换，功能比较相近，这里对他们优缺点做出比较。

这是我用转换工具将上面示例中的 JSON 文本转换成的 XML：

```xml
<?xml version="1.0" encoding="UTF-8"?><root>
  <name>张三</name>
  <age>18</age>
  <address>
    <province>广东省</province>
    <city>广州市</city>
    <street>新港中路XX号</street>
  </address>
  <phoneNumber>
    <type>phone</type>
    <number>020 1234567</number>
  </phoneNumber>
  <phoneNumber>
    <type>telphone</type>
    <number>15602221234</number>
  </phoneNumber>
</root>
```

* 可读性方面。XML 可读性略胜一筹，JSON 可读性也不差。
* 编码解码方面。各个主流的编程语言对 XML 和 JSON 都有成熟的解析库。
* 内容冗余方面。JSON 的内容冗余明显比 XML 少。这是 JSON 的最大优势。这个优势使得 JSON 数据体积小，更适合用于数据网咯传输。