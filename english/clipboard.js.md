# clipboard.js

> 这是著名开源项目 clipboard.js 的 README.md，我把它翻译成中文。发出来，方便自己和他人阅读。
项目地址：https://github.com/zenorocha/clipboard.js

[![Build Status](http://img.shields.io/travis/zenorocha/clipboard.js/master.svg?style=flat)](https://travis-ci.org/zenorocha/clipboard.js)
![Killing Flash](https://img.shields.io/badge/killing-flash-brightgreen.svg?style=flat)

> 现代化的“复制到剪切板”插件。不包含 Flash。gzip 压缩后仅 3kb。

<a href="https://clipboardjs.com/"><img width="728" src="https://cloud.githubusercontent.com/assets/398893/16165747/a0f6fc46-349a-11e6-8c9b-c5fd58d9099c.png" alt="Demo"></a>

## 为什么使用它

复制文字到剪切板不应该很难去实现。它不需要配置几十个步骤或者加载几百 KB 的文件。最重要的是，它不应该依赖 Flash 或其他臃肿的框架。

这是 clipboard.js 诞生的原因。

## 安装

你可以通过 npm 来安装它。

```
npm install clipboard --save
```

如果你不使用包管理，仅需要下载一个 [ZIP](https://github.com/zenorocha/clipboard.js/archive/master.zip) 文件。

## 开始

首先，引入位于 `dist` 目录下的脚本文件，或者引入一个第三方[CDN](https://github.com/zenorocha/clipboard.js/wiki/CDN-Providers)。

```html
<script src="dist/clipboard.min.js"></script>
```

然后，你需要通过传入一个[DOM 选择器](https://github.com/zenorocha/clipboard.js/blob/master/demo/constructor-selector.html#L18), [HTML 元素](https://github.com/zenorocha/clipboard.js/blob/master/demo/constructor-node.html#L16-L17), 或者 [HTML 元素数组](https://github.com/zenorocha/clipboard.js/blob/master/demo/constructor-nodelist.html#L18-L19)作为参数，来实例化对象。

```js
new Clipboard('.btn');
```

本质上，我们需要获取所有选择器匹配到的元素，并为每一个选择器设置监听事件。但仔细想想，如果有成百上千个匹配到的元素，这样做会耗费大量内存。

因此，我们使用[事件代理](http://stackoverflow.com/questions/1687296/what-is-dom-event-delegation)，通过一个事件监听器来取代多个事件监听。毕竟，[性能是问题](https://twitter.com/hashtag/perfmatters)。

## 使用

我们正在经历一场声明式的复兴，这就是为什么我们决定利用 [HTML5 `data` 属性](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_data_attributes) 来提高可用性的原因。

### 从另一个元素复制文本

一个很常见的用例是从另一个元素复制内容。你可以给目标元素添加一个 `data-clipboard-target` 属性来实现这个功能。

这个属性的值就是能匹配到另一个元素的选择器。

<a href="https://clipboardjs.com/#example-target"><img width="473" alt="example-2" src="https://cloud.githubusercontent.com/assets/398893/9983467/a4946aaa-5fb1-11e5-9780-f09fcd7ca6c8.png"></a>

```html
<!-- Target -->
<input id="foo" value="https://github.com/zenorocha/clipboard.js.git">

<!-- Trigger -->
<button class="btn" data-clipboard-target="#foo">
    <img src="assets/clippy.svg" alt="Copy to clipboard">
</button>
```

### 从另一个元素剪切文本

此外，你可以定义一个 `data-clipboard-action` 属性来指明你想要复制（`copy`）还是剪切（`cut`）内容。

如果你省略这个属性，则默认为复制（`copy`）。

<a href="https://clipboardjs.com/#example-action"><img width="473" alt="example-3" src="https://cloud.githubusercontent.com/assets/398893/10000358/7df57b9c-6050-11e5-9cd1-fbc51d2fd0a7.png"></a>

```html
<!-- Target -->
<textarea id="bar">Mussum ipsum cacilds...</textarea>

<!-- Trigger -->
<button class="btn" data-clipboard-action="cut" data-clipboard-target="#bar">
    Cut to clipboard
</button>
```

正如你所预料的，剪切（`cut`）动作只在 `<input>` 或 `<textarea>` 元素起作用。

### 从属性复制文本

事实上，你甚至不需要从另一个元素来复制内容。你仅需要给目标元素设置一个 `data-clipboard-text` 属性就可以了。

<a href="https://clipboardjs.com/#example-text"><img width="147" alt="example-1" src="https://cloud.githubusercontent.com/assets/398893/10000347/6e16cf8c-6050-11e5-9883-1c5681f9ec45.png"></a>

```html
<!-- Trigger -->
<button class="btn" data-clipboard-text="Just because you can doesn't mean you should — clipboard.js">
    Copy to clipboard
</button>
```

## 事件

如果你想要展示一些用户反馈，或者在用户复制/剪切后获取已经选择的文字，这里有个示例供你参考。

我们通过触发自定义事件，例如 `success` 和 `error`，让你可以设置监听并实现自定义逻辑。

```js
var clipboard = new Clipboard('.btn');

clipboard.on('success', function(e) {
    console.info('Action:', e.action);
    console.info('Text:', e.text);
    console.info('Trigger:', e.trigger);

    e.clearSelection();
});

clipboard.on('error', function(e) {
    console.error('Action:', e.action);
    console.error('Trigger:', e.trigger);
});
```

你可以访问这个[网站](https://clipboardjs.com/)，打开控制台，查看演示示例。

## 工具提示（Tooltips）

每个应用有着不同的设计需求，这是为什么 clipboard.js 没有包含任何 CSS 或内置的工具提示解决方案。

你在[示例网站](https://clipboardjs.com/)看到的工具提示是通过 [GitHub's Primer](http://primercss.io/tooltips/) 构建的。如果你正在寻找一个外观和体验类似的库，你可以去看看这个项目。

## 高级选项

如果你不想修改 HTML，我们提供了一个非常方面的命令式的 API 给你使用。你需要做的就是声明一个函数，做一些处理，并返回一个值。

例如，如果你希望动态设置 `target`，你需要返回一个节点（Node）.

```js
new Clipboard('.btn', {
    target: function(trigger) {
        return trigger.nextElementSibling;
    }
});
```

如果你希望动态设置 `text`，你需要返回一个字符串。

```js
new Clipboard('.btn', {
    text: function(trigger) {
        return trigger.getAttribute('aria-label');
    }
});
```

如果在 Bootstrap 模态框（Modals）中使用，或是在其他修改焦点的类库中使用，你会希望将获得焦点的元素设置为 `container` 属性的值。

```js
new Clipboard('.btn', {
    container: document.getElementById('modal')
});
```

同样地，如果你使用单页应用，你可能想要更加精确地管理 DOM 的生命周期。你可以清理事件以及创建的对象。

```js
var clipboard = new Clipboard('.btn');
clipboard.destroy();
```

## 浏览器支持

这个库依赖于 [Selection](https://developer.mozilla.org/en-US/docs/Web/API/Selection) 和 [execCommand](https://developer.mozilla.org/en-US/docs/Web/API/Document/execCommand) 的 API。前者 [兼容所有的浏览器](http://caniuse.com/#search=selection)，后者兼容以下浏览器。

| <img src="https://clipboardjs.com/assets/images/chrome.png" width="48px" height="48px" alt="Chrome logo"> | <img src="https://clipboardjs.com/assets/images/edge.png" width="48px" height="48px" alt="Edge logo"> | <img src="https://clipboardjs.com/assets/images/firefox.png" width="48px" height="48px" alt="Firefox logo"> | <img src="https://clipboardjs.com/assets/images/ie.png" width="48px" height="48px" alt="Internet Explorer logo"> | <img src="https://clipboardjs.com/assets/images/opera.png" width="48px" height="48px" alt="Opera logo"> | <img src="https://clipboardjs.com/assets/images/safari.png" width="48px" height="48px" alt="Safari logo"> |
|:---:|:---:|:---:|:---:|:---:|:---:|
| 42+ ✔ | 12+ ✔ | 41+ ✔ | 9+ ✔ | 29+ ✔ | 10+ ✔ |

好消息是，如果你需要支持旧浏览器，clipboard.js 可以优雅降级。你所要做的就是在 `success` 事件触发时提示用户“已复制！”，`error` 事件触发时提示用户“按 Ctrl+C 复制文字”（此时用户要复制的文字已经选择了）。

你也可以通过运行 `Clipboard.isSupported()` 来检查浏览器是否支持 clipboard.js，如果不支持，你可以隐藏复制/剪切按钮。

## 福利

一个浏览器拓展程序，可以添加一个“复制到剪切板”按钮到所有的代码块，支持 *GitHub，MDN，Gist，StackOverflow，StackExchange，npm，甚至 Medium。*

安装：[谷歌浏览器](https://chrome.google.com/webstore/detail/codecopy/fkbfebkcoelajmhanocgppanfoojcdmg)、[火狐浏览器](https://addons.mozilla.org/en-US/firefox/addon/codecopy/)。

## 协议

[MIT 协议](http://zenorocha.mit-license.org/) © Zeno Rocha
