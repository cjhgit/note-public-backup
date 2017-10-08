# shim 和 polyfill

在前端，有两个词经常被提及：shim 和 polyfill。最近在翻译文章时又遇到了 polyfill 这个词，准备把这两个概念理清楚。

关于 JavaScript 的兼容性问题，通常有不同的解决方案。

举个例子，旧版本的 IE 不支持标准的 XMLHttpRequest，但支持自家的 ActiveXObject 方法，对此有以下两种解决方案。

jQuery 的做法是，把两种方法封装成 `$.ajax` 函数。使用时，只要熟悉 `$.ajax` 方法就可以了，不用考虑浏览器的兼容问题。

```javascript
// 伪代码
$.ajax = function(url) {
    if (isIE) {
        XMLHttpRequest(url)
    } else {
        ActiveXObject(url)
    }
}
```

还有一种方法是，判断浏览器是否支持 XMLHttpRequest，如果不支持，就用 ActiveXObject 实现一个功能跟 XMLHttpRequest 完全一样的函数。

```javascript
// 伪代码
if (!XMLHttpRequest) {
    XMLHttpRequest = function(url) {
        ActiveXObject(url)
    }
}
```

这两种方法看似没什么太大的不同，都能解决跨浏览器的兼容问题。但如果你仔细思考，就会发现，这两种方法代表着两种不同思维方式。后者明显的思想更加先进。

我们来看看这两种做法有什么不同。

1. jQuery 没有遵循标准，这带来了一个学习成本的问题，我们需要学习这个函数的使用方法；而后者在使用上和标准 API 没什么不同，不存在学习成本。
2. 如果某天我们不需要兼容旧 IE 了，后者只要移除兼容代码就可以了，不用改动代码；而前者显然没有这个优势，需要重构代码。遵循标准的代码在维护性方面明显更好。
3. 后者还有个好处是，可以按需加载，只在旧浏览器上加载兼容代码。
4. 标准的代码在可移植性方面也更具优势。

我们再来看看 shim 和 polyfill 的概念。

> shim 是一个库,它将一个新的 API 引入到一个旧的环境中,而且仅靠旧环境中已有的手段实现

polyfill 是 shim 的一种，它的 API 是遵循标准的。polyfill 的做法通常是：先检查浏览器是否支持某个标准 API，如果不支持，就使用旧的技术对浏览器做兼容处理，这样就可以在旧的浏览器上使用新的标准 API。

但在实际情况下，我们一般说 shim，会特指它的 API 不是遵循标准的，与 polyfill 对立。

上面介绍的两种方法，前者是 shim，而后者是 polyfill。polyfill 的设计理念更值得去推崇。

理解了概念后，polyfill 的思想就能指导我们如何去设计 API。

比如说，旧浏览器不支持 ES6 的 `Array.prototype.find` 方法，我们想要在项目中使用 `Array.prototype.find`，只要 polyfill 就行了，而不是封装一个新的方法。

```javascript
// 应该这么做
if (!Array.prototype.find) {
    Array.prototype.find = function() {
        // ...
    }
}
```

```javascript
// 而不是这么做
function arrayFind() {
    if (Array.prototype.find) {
        // ...
    } else {
        // ...
    }
}
```

当然，很多新的 API 的兼容性问题，网上已经有成熟的 polyfill 方案了，不必重复造轮子。

## tmp

CSS polyfill 

Modernizr/Modernizr

溢出文本省略号表示的css实现及polyfill
