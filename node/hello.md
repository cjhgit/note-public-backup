# Node.js 学习笔记 - Hello world

## 前言

这篇文章主要介绍使用 Node.js 运行一个 Hello word 程序。

## 命令行版 helloworld

新建 `index.js`，输入以下内容：

```javascript
console.log("Hello world!")
```

文件所在目录下打开命令行，执行 ``

运行结果：

```text
$ node index.js
Hello world!
```

## Web 版 helloworld

新建 `server.js`：

```javascript
var http = require('http') // 引用 http 库

http.createServer(function (request, response) {

    // 发送 HTTP 头部 
    // HTTP 状态值: 200 : OK
    // 内容类型: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'})

    // 发送响应数据 "Hello World"
    response.end('Hello world\n')
}).listen(80)
```

命令行执行 `node server.js`。

浏览器访问 `http://localhost`，可以看到页面显示：Hello world。

## 附录

项目源码可在 node-hello 文件夹中查看。
