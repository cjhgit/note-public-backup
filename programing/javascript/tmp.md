 
* TypedArray
* javascript Strong Mode

* Math.ceil()：向上取整。
* Math.floor()：向下取整。
* Math.round()：四舍五入取整。

### 基本类型
 
六种数据类型undefined，null，boolean，number、string和object。 
 
 
## ECMAScript 6
 
 
ES6增添了许多必要的特性，例如：模块和类，以及一些实用特性，例如Maps、Sets、Promises、生成器（Generators）等


[各浏览器对ES6的支持](http://kangax.github.io/compat-table/es6/)

windows的子对象：frames[]、history、location、navigator、screen、document。
 


## 预编译

JavaScript在解释执行前，会进行一次“预编译”。
 
1.先预定义用var声明的变量，把这些变量设置为活动对象的属性。然后再预定义以function定义的函数，将这些函数也添加为活动对象的属性，而且他们的值正是函数的定义。
2.变量的预编译只作声明，不作初始化，初始化在执行时。
3.function语句定义的函数，不仅声明了函数名，而且函数体也进行了处理。
4.匿名函数不会预编译。
 

再看看复杂一点的例子：
```javascript
 
function f() { // 普通函数
    return 1;
}

alert(f()); // 返回1
var f = function() { // 匿名函数
    return 2;
}

alert(f()); // 返回2
```

先预定义了变量f，然后同名函数f()覆盖了变量f，所以输出1
再看看另一个类似的例子：

```javascript
var f = function() { // 匿名函数
    return 1;
}

alert(f()); // 返回1

function f() { // 普通函数
    return 2;
}
alert(f()); // 返回1
```
先预定义了变量f,然后同名函数f()覆盖了变量f。
 

```
<script>
document.writeln(a); // 出错
</script>
<script>
var a = 5;
</script>
```



## 作用域
[开发进阶：理解 JavaScript 作用域和作用域链](http://www.cnblogs.com/lhb25/archive/2011/09/06/javascript-scope-chain.html)
 
Javascript的作用域和Java是差不多，但因为Javascript预编译的特殊，导致很容易出错。
 
Javascript没有块作用域
作用域链
 
 
 
原型链
 
 
 


