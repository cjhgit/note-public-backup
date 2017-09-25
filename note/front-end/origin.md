# 跨域

## 什么是同源

如果两个页面具有相同的协议、端口和域名，我们就说这两个页面同源。

比如，对于页面 http://demo.example.com/dir/page 而言：

URL	| 是否同源 | 原因
-- | -- | -- |
http://demo.example.com/dir2/page |	同源 | 
https://demo.example.com/xxx | 不同源 | 协议不同 ( https )
http://demo.example.com:8080/xxx | 不同源 | 端口不同 ( 8080 )
http://demo2.example.com/xxx | 不同源 | 域名不同
http://example.com/xxx | 不同源 | 域名不同
http://111.13.101.28.com/xxx | 不同源 | 域名不同

## 跨域与安全

允许跨域访问是很不安全的，会造成一些安全问题，比如 CSRF（Cross-site request forgery，跨站请求伪造）等。

比如，我利用 `iframe` 把支付宝页面嵌入到我的网站。当用户使用账户和密码登录时，如果没有同源限制，我的页面可以通过 JavaScript 读取到支付宝页面的表单内容，从而获取到用户的账号和密码。

## 同源策略

同源策略（Same-origin policy）是浏览器采用的一种安全策略，它限制从一个源（origin）加载的文档或脚本如何与来自另一个源的资源进行交互。

对于两个不同源的页面，他们加载的文档或脚本不能进行交互。比如：一个页面加载的 JavaScript 代码不能修改另一个非同源页面的 Cookie。

由于同源策略只是浏览器采用的一种策略，所以在非浏览器环境下，比如服务器请求或者其他客户端请求，不存在跨域这一说法。

同时，同源策略也只是浏览器的一个“君子协定”，并不是强制性要求。但目前所以主流的浏览器都支持这个协定，虽然在细节上可能存在差异。

## 修改源

我们可以通过 `document.domain` 来修改页面的源。当然，这功能是有限制，不然同源策略就形同虚设了。

我们可以在 demo.example.com 的页面通过 `document.domain = 'example.com'` 来设置页面的源为 example.com。但是不能在 `example.com` 的页面设置源为 `demo.example.com`。

## 跨域访问（Cross-origin network access）

同源策略提高了网页的安全性，但同时也给开发到来了很多麻烦。跨域访问的例子很常见，比如，网站开发了接口给第三方网页端使用；再如，前后端分离时，网站和接口位于不同的子域名。

这时，我们就需要跨域访问。所谓的跨域，就是指跨源，即不同源之间的资源能够相互交互。

下面介绍常用的跨域解决方案。

### CORS

CORS（Cross-origin resource sharing，跨域资源共享）是一个 W3C 标准，它允许浏览器向跨源服务器发出 XMLHttpRequest 请求。

缺点：

* 对旧浏览器兼容不好，需要 IE10+。

### JSON-P

JSON-P（JSON with padding）也是常用的跨域解决方案。JSON-P 本质上是一个“hack”，利用 `script` 元素不受同源策略的限制，把数据按照某种约定好的格式存放到 JavaScript 脚本中。然后再动态创建 `script` 元素，执行返回的 JavaScript 代码，从而获取代码里面的数据。

缺点：

* 只支持 `GET` 请求。

### 服务器中转

没什么好说的，就是服务器请求跨域资源，间接把数据传给前端。

### postmessage 跨域





## tmp

CORS 可以带上cookie的， 配置withCredentials即可

> CORS 跨域似乎需要 IE10+ 才支持的
最近刚好接手一个跨域的功能，在 IE9 下测试失败，IE10 就可行

对于浏览器来说，除了DOM、Cookie、XMLHttpRequest 会受到同源策略的限制外，浏览器加载的一些第三方插件也有各自的同源策略。最常见的一些插件如 Flash、Java Applet、Silverlight、Google Gears等都有自己的控制策略。

ie8+ IE里可以使用XDomainRequest这个来实现CORS

header('Access-Control-Allow-Origin: 好像能只能指定单个域名







## Cookie 跨域

服务端：

```
Access-Control-Allow-Origin: *
Access-Control-Allow-Credentials: true
```

浏览器端：


在跨域的情况下使用 axios，首先需要配置 axios 的 withCredentials 属性为 true。

