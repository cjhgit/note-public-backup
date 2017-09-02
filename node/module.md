# Node.js 学习笔记 – 模块化

## 前言

模块化是大型应用程序架构中不可缺少的一部分，模块化可以使我们清晰地分离和组织代码，让项目更好的维护。

其他编程语言，大部分都自带模块化的功能，比如 Java 的 `import`、C# 的 `using` 以及 C 语言的 `include`。

在 ES6 出来之前，JavaScript 是不支持模块化的。非官方的模块化解决方案有三种：node 的 CommonJS 规范，requirejs 的 AMD 规范以及 seajs 的 CMD 规范。

ES6 出来后，这三种模块化方案就变成过时的玩意了。逐渐被淘汰。但由于 ES6 的姗姗来迟，V8 引擎暂时还不支持 ES6 模块化方案，基于 V8 引擎的 Node.js 自然也就不支持 ES6 模块化。因为还需要学习 CommonJS 这种即将淘汰的模块化方案。

## 开始

还是写一个 Hello world 示例。

`index.js`：

```
let hello = require('./hello')
hello()
```

`hello.js`：

```
module.exports = function() {
	console.log('Hello world!')
}
```

命令行执行 `node index.js`：

```
$ node index.js
Hello world!
```

在 CommonJS 规范中，每一个文件就是一个模块。`module` 表示当前模块，`module.exports` 表示当前模块导出的对象。而在其他文件引用（require）这个模块，其实就是引用 `module.exports` 对象。

在示例 `hello.js` 中，`module.exports` 赋值为一个函数，表示该模块导出对象是一个函数；`index.js` 导入该函数，便可直接使用该函数。

// TODO 未完待续

