# 前端

前端知识体系
    
* [HTML](/html.md)
* [CSS](/css.md)
* [JavaScript](/javascript.md)

* 优雅降级（graceful degradation）、渐进增强（progressive enhancement）
* [shim 和 polyfill](/front-end/polyfill-and-shim.md)
* web app v.s. native app
    * hybrid App（混合 App）
    * 微信小程序
    * PWA（Progressive Web App）

app_shell
    
第三方统计：

* 百度统计
* CNZZ

第三方分享：

* 百度分享

网页打赏：

* https://github.com/greedying/tctip

第三方社会化评论：

* 友言
* 畅言
* ~~网易云跟帖~~
* ~~多说~~

第三方点赞

工具

* gulp
* webpack
* grunt


* XPath
* XMLHttpRequest
* fetch API
* ServiceWorker

* commander.js




在 Github 搜索 JavaScript，按 stars 排序：

1. freeCodeCamp
2. bootstrap
3. react
4. You-Dont-Know-JS.
5. vue
6. javascript
7. electron
8. jquery
9. atom
10. node
11. html5-boilerplate
12. meteor
13. three.js
14. redux
15. express
16. moment
17. nw.js
18. Chart.js
19. webpack
20. ionic
21. materialize
22. material-ui
23. brackets
24. angular
25. yarn
26. axios
27. lodash
28. TypeScript
29. Ghost
30. nylas-mail
31. babel
32. async
33. free-programming-books-zh_CN
34. underscore
35. select2
36. Modernizr
37. fullPage.js
38. echarts
38. immutable-js
40. Leaflet
41. pdf.js
42. clipboard.js
43. hyper
44. awesome-nodejs
45. ember.js
46. hexo
47. freecodecamp.cn
48. video.js
49. skrollr
50. RxJS



Tweene-超级强大的jQuery动画代理插件

font-carrier
panda-master
handsontable-master
paper.js-develop


用到的框架或类库：

* [mzabriskie/axios](https://github.com/mzabriskie/axios)

* Parallax
* TheaterJS
* leaflet-echarts-master
* canvax-master
* uploader-master
* leaflet-pip-v2-master
* threejs-earth-master
* Vue.Draggable-case-master
* JasonAmbition-master
* viewer-master
* ssite-master
* sliptree-bootstrap-tokenfield-9c06df4
* WebCraft-master
* Simple-Overlay-master
* WebCraft-master
* zenpen-master
* V8 编译器

application/x-www-form-urlencoded：窗体数据被编码为名称/值对。这是标准的编码格式。这是默认的方式
multipart/form-data：窗体数据被编码为一条消息，页上的每个控件对应消息中的一个部分。二进制数据传输方式，主要用于上传文件
text/plain：窗体数据以纯文本形式进行编码，其中不含任何控件或格式字符。


jQuery 地区选择

三级联动
https://github.com/fengyuanchen/distpicker

仿淘宝地区选择
https://github.com/tshi0912/city-picker

## 前端优化

图片压缩
https://tinypng.com/

tinypng API + gulp

epub.js

https://github.com/futurepress/epub.js

node.js epub reader
https://github.com/julien-c/epub

## HTML5 拍照上传

## Web Intents

> 我觉得Web intents相当于标准版的ifttt，不过ifttt的关注点相对于Web intents还有所不同

> 混聚（Mashup）是一种基于Web Services、资源元数据规范等技术的网络应用开发技术，它可以将不同站点或应用程序的数据、资源、API加以混聚来构建新的业务流程，满足新的用户需求。混聚的思想最早启迪于艺术领域，现已作为一种网络应用开发模式为世人所熟知。

Web Intents是个相对较新的类似于RPC的机制，可以实现Web应用间的通信，这是通过在客户端（通常但不限于是网页）与服务（如网页、扩展API、插件、OS处理器等，知道如何处理与加工各自的数据）之间传递数据并返回结果来实现的。整个过程是由User Agent（通常是浏览器）来处理的，它让用户决定由哪个服务来执行与Intent相关的动作。Web Intents类似于Android Intents，最初是由Google在去年提出的，现已被W3C接受为草案文档，并希望包含在HTML.Next中

<intent    action="http://webintents.org/share"    type="image/>

var intent = new Intent(      "http://webintents.org/share",      "image/",      "http://example.com/image.png"  ); window.navigator.startActivity(intent);

http://www.infoq.com/cn/news/2012/05/Web-Intents

## 国际化

jQuery国际化插件依据RFC 4646和RFC 5646标准里定义的语言标记来识别文化，语言标记通常由连字符将多个辅标签组合而成，比如

## notification std.
https://www.html5rocks.com/en/tutorials/notifications/quick/

## extensions

文档
https://developer.chrome.com/extensions/api_index
http://open.chrome.360.cn/extension_dev/themes.html
https://chajian.baidu.com/developer/extensions/api_index.html

如何模拟扩展唯一的ID
http://blog.csdn.net/talking12391239/article/details/44996033

讲解插件文章
http://blog.mn886.net/chenjianhua/show/3f02d7463ede/index.html

ChromeTheme–在线制作个性Chrome主题

