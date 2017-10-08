> 这是著名开源项目 FileSaver.js 的 README.md，我把它翻译成中文。发出来，方便自己和他人阅读。
项目地址：[https://github.com/eligrey/FileSaver.js](https://github.com/eligrey/FileSaver.js)

如果你需要保存较大的文件，不受 blob 的大小限制或内存限制，可以看一下更高级的 [StreamSaver.js](https://github.com/jimmywarting/StreamSaver.js)，
它使用强大的 stream API，可以将数据直接异步地保存到硬盘。支持进度、取消操作以及完成事件回调。

FileSaver.js
============

FileSaver.js 在没有原生支持 `saveAs()` 的浏览器上实现了 `saveAs()` 接口。有一个 [FileSaver.js 示例][1]，演示如何保存各种媒体类型。

FileSaver.js 是在客户端保存文件的解决方案，非常适合需要生成文件，或者保存不应该发送到外部服务器的敏感信息的 web App。

你还在寻找 `canvas.toBlob()` 来保存画布？[canvas-toBlob.js][2] 可以跨浏览器实现这个功能。

支持的浏览器
------------------

| Browser        | Constructs as | Filenames    | Max Blob Size | Dependencies |
| -------------- | ------------- | ------------ | ------------- | ------------ |
| Firefox 20+    | Blob          | Yes          | 800 MiB       | None         |
| Firefox < 20   | data: URI     | No           | n/a           | [Blob.js](https://github.com/eligrey/Blob.js) |
| Chrome         | Blob          | Yes          | [500 MiB][3]  | None         |
| Chrome for Android | Blob      | Yes          | [500 MiB][3]  | None         |
| Edge           | Blob          | Yes          | ?             | None         |
| IE 10+         | Blob          | Yes          | 600 MiB       | None         |
| Opera 15+      | Blob          | Yes          | 500 MiB       | None         |
| Opera < 15     | data: URI     | No           | n/a           | [Blob.js](https://github.com/eligrey/Blob.js) |
| Safari 6.1+*   | Blob          | No           | ?             | None         |
| Safari < 6     | data: URI     | No           | n/a           | [Blob.js](https://github.com/eligrey/Blob.js) |
| Safari 10.1+   | Blob          | Yes          | n/a           | None         |

支持特征检测:

```js
try {
    var isFileSaverSupported = !!new Blob;
} catch (e) {}
```

### IE < 10

可以在 IE < 10 的浏览器实现保存文本文件，而不需要基于 Flash 的 polyfill。
点击 [ChenWenBrian and koffsyrup's `saveTextAs()`](https://github.com/koffsyrup/FileSaver.js#examples) 查看更多详情。

### Safari 6.1+

有时候 Blob（要保存的文件） 可能会被浏览器直接打开而不是保存，如果文件在浏览器上打开了，你需要指导 Safari 用户手动按 ⌘ + S 保存文件。 使用 `application/octet-stream` MIME 类型强制下载在 Safari 会导致[出现问题](https://github.com/eligrey/FileSaver.js/issues/12#issuecomment-47247096)。

### iOS

saveAs 必须在用户交互事件（如 onTouchDown 或 onClick）中运行; setTimeout 会阻止 saveAs 触发。 由于 iOS 的限制，saveAs 会打开新窗口而不是下载，
如果您想修复这个问题，请[告诉苹果](https://bugs.webkit.org/show_bug.cgi?id=102914)这个 bug 是如何影响你的。

语法
------

```js
FileSaver saveAs(Blob/File data, optional DOMString filename, optional Boolean disableAutoBOM)
```

如果不希望 FileSaver.js 自动提供 Unicode 文本编码提示（参见：[字节顺序标记](https://en.wikipedia.org/wiki/Byte_order_mark)），请将 disableAutoBOM 参数设置为 true。

示例
--------

### 使用 require 保存文本

```js
var FileSaver = require('file-saver');
var blob = new Blob(["Hello, world!"], {type: "text/plain;charset=utf-8"});
FileSaver.saveAs(blob, "hello world.txt");
```

### 保存文本

```js
var blob = new Blob(["Hello, world!"], {type: "text/plain;charset=utf-8"});
saveAs(blob, "hello world.txt");
```

标准 W3C 文件 API [`Blob`][4] 接口不兼容所有浏览器。
[Blob.js][5] 是一个跨浏览器的 `Blob` 实现，可以解决兼容性问题。

### 保存画布（canvas）

```js
var canvas = document.getElementById("my-canvas"), ctx = canvas.getContext("2d");
// draw to canvas...
canvas.toBlob(function(blob) {
    saveAs(blob, "pretty image.png");
});
```

注意：标准的 HTML5 `canvas.toBlob()` 方法不兼容所有浏览器。
[canvas-toBlob.js][6] 是一个跨浏览器的实现 `canvas.toBlob()` 的 polyfill 方案。

### 保存文件

你可以保存一个文件结构，不需要指定文件名。文件自身已经包含了文件名，有一些方法来获取文件实例（从 storage，file input，新的构造函数）
如果你想修改文件名，你可以在第二个参数设置文件名。

```js
var file = new File(["Hello, world!"], "hello world.txt", {type: "text/plain;charset=utf-8"});
saveAs(file);
```



![Tracking image](https://in.getclicky.com/212712ns.gif)

  [1]: http://eligrey.com/demos/FileSaver.js/
  [2]: https://github.com/eligrey/canvas-toBlob.js
  [3]: https://code.google.com/p/chromium/issues/detail?id=375297
  [4]: https://developer.mozilla.org/en-US/docs/DOM/Blob
  [5]: https://github.com/eligrey/Blob.js
  [6]: https://github.com/eligrey/canvas-toBlob.js

贡献
------------

`FileSaver.js` 的发布文件使用 Uglify.js 编译生成，就像这样：

```bash
uglifyjs FileSaver.js --mangle --comments /@source/ > FileSaver.min.js
# or simply:
npm run build
```

在提交请求之前，请确保已经生成了生产版本。

安装
------------------

```bash
npm install file-saver --save
bower install file-saver
```

此外，如果要安装 Typscript 声明，可以这样做：

```bash
npm install @types/file-saver --save-dev
```