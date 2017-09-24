# 函数式编程

## 编程范式

编程范式（Programming paradigm）

* 声明式编程（Declarative Programming）
    * 函数式编程（Functional programming）
    * 面向切面编程（Aspect Oriented Programming，简称AOP）
    * SQL
* 命令式编程（Imperative programming）
    * 面向过程编程（Procedural programming）
    * 面向对象编程（Object-oriented programming）
    
面向协议编程


弱类型、强类型、动态类型、静态类型

## 概念

* 函数是“一等公民”（First-class function）
* 只使用纯函数（Pure Function）
* 高阶函数（higher order function）
* 函数柯里化（curry）


组合（compose）


函子（functor）
（monad）


React的设计贯彻了声明式编程（Declarative Programming）的思想



haskell
monad lifting


 continuation， monad 和 uniqueness typing（一致型别）
 
 学函数式语言，基本都会遇到map, reduce, filter, zip这些经典的高阶函数。

 
 
 ## JavaScript 函数式编程
 
 * 禁用var/let，所有东西都用const定义，也就是说无变量，强制immutable。
 * 禁用分号，也就是不让“顺序执行”，解除过程式编程范式。
 * 禁用if/else，但允许用条件表达式condition ? expr1 : expr2。
 * 禁用for/while/do-while。
 * 禁用prototype和this来解除JS中的面向对象编程范式。
 * 禁用function和return关键字，仅用lambda表达式来编程（JS里叫箭头函数）。
 * 禁用多参数函数，只允许使用单个参数，相当于强行curry化
 
 
 实现for循环遍历数组：
 
 ```javascript

```
 
 ```javascript
function map(arr, callback, i) {
    i < arr.length ?
        
    if (i < arr.length) {
        callback(arr[i])
        map(arr, callback, i + 1)
    }
}

const arr = [1, 2, 3, 0, 6]
map([1, 2, 3, 0, 6], item => console.log(item), 0) // 1 2 3 0 6
```

```javascript
let add = (a, b) => a + b

add(1, 2) // 3
```

```javascript
const add = x => (y => x + y)
add(1)(2) // 3
```



```
function sum(x){ 
   var y = function(x){ 
       return sum(x+y) 
   } 
   y.toString = y.valueOf = function(){ 
     return x; 
  } 
   return y; 
}  
```

```
var s = sum(1)(2)(3)(4);
alert(s); // 10
```