# （译）通过 HTML、JS 和 Electron 创建你的第一个桌面应用

原文：[Creating Your First Desktop App With HTML, JS and Electron](https://tutorialzine.com/2015/12/creating-your-first-desktop-app-with-html-js-and-electron)
作者：[Danny Markov](https://tutorialzine.com/@danny)

近年来 web 应用变得越来越强大，但是桌面应用仍然有充分利用硬件的优势。

今天，我们可以通过我们熟悉的 HTML、JS 和 Node.js 来创建桌面应用，打包成一个可执行文件，并且发布在 Windows, OS X 和 Linux 上。

有两个受欢迎的开源项目，能够帮助我们实现这个目的。一个是几个月前我们[讨论](https://tutorialzine.com/2015/01/your-first-node-webkit-app/)到的 [NW.js](http://nwjs.io/)，另一个是今天我们将要使用的 Electron（点击[这里](https://github.com/atom/electron/blob/master/docs/development/atom-shell-vs-node-webkit.md)查看它们的不同之处）。我们将把旧项目的 NW.js 重构成 Electron，所以你可以轻松地比较他们的不同。

## 开始使用 Electron

用 Electron 构建的应用仅仅是一个网站而已，这个网站在嵌入了 Chromium 的浏览器中运行。除了常规的 HTML5 接口，这些应用能够使用所有的 Node.js 模块，以及 Electron 特有的模块，这个模块能够让应用拥有访问操作系统的能力。

这篇文章中，我们将会构建一个简单的应用，通过 RSS 订阅，来获取 Tutorialzine 上最新的文章，并通过好看的轮播的形式展现出来。这个项目用到的所有文件，你可以点击文章顶部的下载按钮获取（译者注：[下载链接](https://demo.tutorialzine.com/2015/12/creating-your-first-desktop-app-with-html-js-and-electron/creating-your-first-desktop-app-with-electron.zip)）。

下载后，解压内容到一个文件夹。从文件结构来看，你永远猜不到这是一个桌面应用，而不仅仅是一个简单的网站。

![目录结构](https://tutorialzine.com/media/2015/12/electron-app-tree.png)

接下来，我们将仔细分析这些项目文件，了解它们是如何工作的。但首先，我们来运行这个应用。

## 运行应用

由于 Electron 应用只是一个 Node.js 应用，你需要安装 [npm](https://www.npmjs.com/)。你可以点击[这里](http://blog.npmjs.org/post/85484771375/how-to-install-npm)学习怎样安装，这很容易。

解压项目后，在解压目录下打开 cmd 或者命令行，执行以下命令：

```
npm install
```

这条命令会创建一个 `node_modules` 文件夹，里面包含了项目需要所有的 Node.js 依赖。接下来，在同个终端上执行下面的命令：

```
npm start
```

这个应用会打开一个新的窗口。注意看，窗口有一个顶部菜单以及其他东西。

![](https://tutorialzine.com/media/2015/12/electron_app_1.png)

你可能已经留意到，这个应用的启动方式不怎么友好。但这仅仅是开发时启动应用的方式。应用打包发布后，就会像普通的程序那样只是一个安装文件，双击图标就可以启动。

## 它是如何工作的

这一段内容，我们将讨论 Electron 应用必要的文件。我们将从 `package.json` 文件讲起，这个文件包含关于这个项目的各种信息，比如版本号、npm 依赖以及其他重要的配置。

```
package.json

{
  "name": "electron-app",
  "version": "1.0.0",
  "description": "",
  "main": "main.js",
  "dependencies": {
    "pretty-bytes": "^2.0.1"
  },
  "devDependencies": {
    "electron-prebuilt": "^0.35.2"
  },
  "scripts": {
    "start": "electron main.js"
  },
  "author": "",
  "license": "ISC"
}
```

如果你之前使用过 Node.js，你已经知道了这个文件是做什么的。在这里最值得讲述的是 `scripts` 这个属性，它定义了 `npm start` 这条命令，允许我们使用命令来运行应用。当我们执行这条命令的时候，electron 就会执行 `main.js`。这个 JS 文件的脚本打开了应用的窗口，定义了一些配置和事件处理。

### main.js

```
var app = require('app');  // Module to control application life.
var BrowserWindow = require('browser-window');  // Module to create native browser window.

// Keep a global reference of the window object, if you don't, the window will
// be closed automatically when the JavaScript object is garbage collected.
var mainWindow = null;

// 当所有窗口关闭时退出应用
app.on('window-all-closed', function() {
    // On OS X it is common for applications and their menu bar
    // to stay active until the user quits explicitly with Cmd + Q
    if (process.platform != 'darwin') {
        app.quit();
    }
});

// This method will be called when Electron has finished
// initialization and is ready to create browser windows.
app.on('ready', function() {
    // 创建浏览器窗口
    mainWindow = new BrowserWindow({width: 900, height: 600});

    // 加载这个应用的 index.html
    mainWindow.loadURL('file://' + __dirname + '/index.html');

    // 当窗口关闭时执行
    mainWindow.on('closed', function() {
        // Dereference the window object, usually you would store windows
        // in an array if your app supports multi windows, this is the time
        // when you should delete the corresponding element.
        mainWindow = null;
    });
});
```

我们来看一下，在 `ready` 方法做了哪些事情。首先我们定义了一个浏览器窗口，并且设置了它的初始化大小。然后，在窗口里面加载了 `index.html` 文件，这一步就像在浏览器中打开了一个 HTML 文件。

正如你所看到的，这个 HTML 文件本身并没有什么特别——它包含了一个轮播组件的容器标签和一个用来展示 CPU 和 RAM 的 `p` 标签。

### index.html

```
<!DOCTYPE html>
<html>
<head>

    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <title>Tutorialzine Electron Experiment</title>

    <link rel="stylesheet" href="./css/jquery.flipster.min.css">
    <link rel="stylesheet" href="./css/styles.css">

</head>
<body>

<div class="flipster">
    <ul>
    </ul>
</div>

<p class="stats"></p>

<!-->In Electron, this is the correct way to include jQuery<-->
<script>window.$ = window.jQuery = require('./js/jquery.min.js');</script>
<script src="./js/jquery.flipster.min.js"></script>
<script src="./js/script.js"></script>
</body>
</html>
```

这个 HTML 文件也引用了几个必要的样式文件，JS 库和脚本。注意在这里 jQuery 是通过一种奇怪的方式引入进来的。更多相关信息可以查看这个[issue](http://stackoverflow.com/questions/32621988/electron-jquery-is-not-defined)。

最后，是这个应用的实际脚本文件。脚本里面，我们调用 Tutorialzine 的 RSS 订阅接口，获取了最新的文章并且展示出来。如果我们在浏览器环境这么做，是获取不到数据的，因为跨域的原因，我们无法获取到数据。但在 Electron 里就没有跨域的限制，我们可以简单地通过 AJAX 请求来获取我们需要的信息。

```
$(function(){

    // Display some statistics about this computer, using node's os module.

    var os = require('os');
    var prettyBytes = require('pretty-bytes');

    $('.stats').append('Number of cpu cores: <span>' + os.cpus().length + '</span>');
    $('.stats').append('Free memory: <span>' + prettyBytes(os.freemem())+ '</span>');

    // Electron's UI library. We will need it for later.

    var shell = require('shell');

    // 获取 Tutorialzine 上最新的文章

    var ul = $('.flipster ul');

    // The same-origin security policy doesn't apply to electron, so we can
    // send ajax request to other sites. Let's fetch Tutorialzine's rss feed:

    $.get('http://feeds.feedburner.com/Tutorialzine', function(response){

        var rss = $(response);

        // Find all articles in the RSS feed:

        rss.find('item').each(function(){
            var item = $(this);

            var content = item.find('encoded').html().split('</a></div>')[0]+'</a></div>';
            var urlRegex = /(http|ftp|https):\/\/[\w\-_]+(\.[\w\-_]+)+([\w\-\.,@?^=%&amp;:/~\+#]*[\w\-\@?^=%&amp;/~\+#])?/g;

            // Fetch the first image of the article.
            var imageSource = content.match(urlRegex)[1];

            // Create a li item for every article, and append it to the unordered list.

            var li = $('<li><img /><a target="_blank"></a></li>');

            li.find('a')
                .attr('href', item.find('link').text())
                .text(item.find("title").text());

            li.find('img').attr('src', imageSource);

            li.appendTo(ul);

        });

        // Initialize the flipster plugin.

        $('.flipster').flipster({
            style: 'carousel'
        });

        // 文章被点击时，在系统默认浏览器打开连接
        // 不这样做的话，会在 electron 窗口中打开连接，这不是我们想要的效果

        $('.flipster').on('click', 'a', function (e) {

            e.preventDefault();

            // 在默认浏览器中打开链接

            shell.openExternal(e.target.href);

        });

    });

});
```

上面的代码中，比较酷的是，我们在一个文件同时使用了：

* JavaScript 库 - 使用 jQuery 和 jQuery Flipster 来生成轮播效果。
* Electron 原生模块 - Shell 这个模块提供了桌面相关的任务接口，在示例中，我们通过这个接口调用默认浏览器中打开了一个链接。
* Node.js 模块 - 用来访问操作系统信息的 OS 模块，用来格式化的 Pretty Bytes 模块。通过这些模块，我们完成了这个应用!

## 打包和发布

还有一件重要的事需要我们去做，就是准备好我们的应用给最终用户使用。你需要把项目打包成一个可执行文件，可以在用户的机器上双击运行。由于 Electron 应用可以在多个不同的操作系统上运行，我们需要分别打包成 Windows、OS X 和 Linux 各个版本。像 Electron Packager 这个 npm 模块就是一个不错的工具。

需要考虑的是，打包项目时会把所有资源，所有的 Node.js 依赖，加上一个缩小版的 WebKit 浏览器，打包成一个可执行的文件。这些东西加起来的结果就是，打包后的应用体积大约为 50mb。这个体积已经算是比较大了，对于一些简单的应用，比如这个示例项目来说，有些不太理想。但对于那些比较大而又复杂的项目来说，就无关紧要了。

## 总结

从这个示例项目可以看出，Electron 与 NW.js 的主要差异在于，NW.js 是直接打开一个 HTML 页面，而 Electron 是通过执行一个脚本文件，在代码中创建一个窗口。Electron 这种创建方式，能够让我们更大程度地控制应用，比如我们可以轻松地构建一个多窗口应用，并在窗口之间进行通信。

整体上，Electron 是一个令人激动的、通过 web 技术来构建桌面应用的方式。接下来，你可以继续阅读：

* [Electron 快速入门](https://github.com/atom/electron/blob/master/docs/tutorial/quick-start.md)
* [Electron 文档](https://github.com/atom/electron/tree/master/docs)
* [用 Electron 构建的应用](http://electron.atom.io/#built-on-electron)

## 我（译者）的总结

* 翻译这篇文章，主要是因为这篇文章已经有中文译文了，翻译完成后，我可以对比[其他译文](https://github.com/xitu/gold-miner/blob/master/TODO/creating-your-first-desktop.md)，总结不足之处。对比了一下，差距还是很大的。
* 翻译到一半才发现，运行效果和文中的截图不一致。调试发现，是因为 Tutorialzine 的接口不能用了。这导致翻译出来的文章实用性大大降低，这一点，以后需要注意。
* 文章没有讲到如何打包 Electron 应用，有点可惜。有时间我会补充，或者另写一篇。
* 一年前就接触了 Electron，当时 Electron 还有很多不足，现在 Electron 改进了一些，比较看好 Electron 的发展。
* 这是我的第一篇翻译，万事开头难，中间更难，结尾最难，还需继续努力。


