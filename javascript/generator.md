# Generator

在学习 Generator 之前，你需要先了解[迭代器](iterator.md)相关的知识，以便能更好地理解本文。

生成器函数（Generator function）是 ES6 的一个新的特性。概念不好讲解，我们可以从一个示例来了解它。

```javascript
function* f() {
    console.log('before yield 1')
    yield 1
    console.log('before yield 2')
    yield 2
    console.log('before return')
    return 3
}

f()
```

生成器函数的定义和函数类似，只不过在 `function` 后多了一个星号（*）。对于学过 C++ 的，看到这种语法有种熟悉感，只不过在 JavaScript，这种写法不是返回指针的意思。 

记得当初学习 C++ 时，曾纠结过在星号前空格还是星号后空格。我习惯在星号后空格，当然星号前后都空格也是允许的。

如果你执行上面的示例，你会发现控制台并没有输入任何东西。

如果我们这样写：

```javascript
var g = f()
console.log(g.next()) // Object {value: 1, done: false}
```

就可以看到控制台输出：

```text
before yield 1
Object {value: 1, done: false}
```

熟悉迭代器的看到这里应该会焕然大悟：原来生成器函数返回的是一个迭代器。我们继续执行 `next' 函数：

```javascript
var g = f()
console.log(g.next())
console.log(g.next())
```

控制台输出：

```text
before yield 1
Object {value: 1, done: false}
before yield 2
Object {value: 2, done: false}
```

执行 `next' 函数：

```javascript
var g = f()
console.log(g.next())
console.log(g.next())
console.log(g.next())
```

控制台输出：

```text
before yield 1
Object {value: 1, done: false}
before yield 2
Object {value: 2, done: false}
before return
Object {value: 3, done: true}
```

看到这里，我想你应该明白了，生成器函数执行后，返回一个迭代器。执行 `next` 方法后，函数会执行直到遇到 yield 语句或 return 语句。如果函数只执行到 yield 语句，便返回不再继续执行，下一次执行 `next` 方法时，函数会从上一次停止的地方开始执行。所以才说，生成器函数能够多次返回值。

