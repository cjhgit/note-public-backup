

一、文件规范

1、文件均归档至约定的目录中。

具体要求通过豆瓣的CSS规范进行讲解：

所有的CSS分为两大类：通用类和业务类。通用的CSS文件，放在如下目录中：

基本样式库 /css/core 

通用UI元素样式库 /css/lib 

JS组件相关样式库 /css/ui 

业务类的CSS是指和具体产品相关的文件，放在如下目录中：

读书 /css/book/ 

电影 /css/movie/ 

音乐 /css/music/ 



外联CSS文件适用于全站级和产品级通用的大文件。内联CSS文件适用于在一个或几个页面共用的CSS。另外一对具体的CSS进行文档化的整理。如：



modernizr-2.6.2.min.js


带前缀的属性
当使用特定厂商的带有前缀的属性时，通过缩进的方式，让每个属性的值在垂直方向对齐，这样便于多行编辑。
 
在 Textmate 中，使用 Text → Edit Each Line in Selection (⌃⌘A)。在 Sublime Text 2 中，使用 Selection → Add Previous Line (⌃⇧↑) 和 Selection → Add Next Line (⌃⇧↓)。

/* Prefixed properties */
.selector {
    -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
                box-shadow: 0 1px 2px rgba(0,0,0,.15);
}





Less 和 Sass 中的嵌套
避免非必要的嵌套。这是因为虽然你可以使用嵌套，但是并不意味着应该使用嵌套。只有在必须将样式限制在父元素内（也就是后代选择器），并且存在多个需要嵌套的元素时才使用嵌套。

// Without nesting
.table > thead > tr > th { … }
.table > thead > tr > td { … }
 
// With nesting
.table > thead > tr {
  > th { … }
  > td { … }
}


破折号应当用于相关 class 的命名（类似于命名空间）（例如，.btn 和 .btn-danger）。



class 名称应当尽可能短，并且意义明确。

只有在必要的时候才将 class 限制在最近的父元素内（也就是后代选择器）（例如，不使用带前缀的 class 时 -- 前缀类似于命名空间）。


代码组织
以组件为单位组织代码段。
制定一致的注释规范。

如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动。



不要使用表现形式（presentational）的名称。
基于最近的父 class 或基本（base） class 作为新 class 的前缀。
使用 .js-* class 来标识行为（与样式相对），并且不要将这些 class 包含到 CSS 文件中。

对于经常出现的组件，避免使用属性选择器（例如，[class^="..."]）。浏览器的性能会受到这些因素的影响。

href="javascript:void(0)"

背景图片 背景颜色

有两种类型的字体系列名称：
指定的系列名称：具体字体的名称，比如："times"、"courier"、"arial"。
通常字体系列名称：比如："serif"、"sans-serif"、"cursive"、"fantasy"、"monospace"
提示：使用逗号分割每个值，并始终提供一个类族名称作为最后的选择。


17.清除浮动的几种方式，各自的优缺点
1.使用空标签清除浮动 clear:both（理论上能清楚任何标签，，，增加无意义的标签）
2.使用overflow:auto（空标签元素清除浮动而不得不增加无意代码的弊端,,使用zoom:1用于兼容IE）
3.是用afert伪元素清除浮动(用于非IE浏览器)



## 绘图
 
做了个小Demo（做的时候没考虑兼容性，非最新浏览器不要看了）：
 
[demo] http://www.chenjianhang.com/demo/dark/ [/demo]
 
比较实用的css小技巧：
 
椭圆：
 
```css
.test {
width: 200px;
height: 100px;
background: red;
-moz-border-radius: 100px / 50px;
-webkit-border-radius: 100px / 50px;
border-radius: 100px / 50px;
}
```
 
上三角：
 
```css
.test {
width: 0;
height: 0;
border-left: 50px solid transparent;
border-right: 50px solid transparent;
border-bottom: 100px solid red;
}
```
 
左上三角
 
```css
.test {
width: 0;
height: 0;
border-top: 100px solid red;
border-right: 100px solid transparent;
}
```
 
同理，还有下三角，左下三角什么的，自己去想。
 
提示对话框
 
```css
.test {
width: 120px;
height: 80px;
background: red;
position: relative;
-moz-border-radius: 10px;
-webkit-border-radius: 10px;
border-radius: 10px;
}
.test:before {
content:"";
position: absolute;
right: 100%;
top: 26px;
width: 0;
height: 0;
border-top: 13px solid transparent;
border-right: 26px solid red;
border-bottom: 13px solid transparent;
}
```
 
这个很实用
 
鸡蛋形状：
 
```css
 
.test {
display:block;
width: 126px;
height: 180px;
background-color: red;
-webkit-border-radius: 63px 63px 63px 63px / 108px 108px 72px 72px;
border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
}
 
```
 
这个可以用来做交互动画。
 
## 兼容性
 
说到CSS3，就不得不提兼容性；说到兼容性，就不得不提IE（万恶的IE，用户习惯真可怕）。
 
**CSS3 选择器**：除了 IE9 以下的版本（不包括IE9），其它浏览器已全部支持 CSS3 选择器。
 
**CSS3 属性**：
 
[![2012071115060164](http://www.chenjianhang.com/wp-content/uploads/2016/01/2012071115060164-203x300.jpg)](http://www.chenjianhang.com/wp-content/uploads/2016/01/2012071115060164.jpg)
 
（图片来自互联网，很多站点都有，找不到出处）
 
其他特性没时间研究了，给个链接自己去看：
 
[各大浏览器 CSS3 和 HTML5 兼容速查表](http://tools.yesky.com/233/30105733.shtml)
 
虽然兼容性略坑，但HTML5+CSS3已经逐渐成为主流了，兼容性的解决方案还是有的，改天再写。
 
#### border-radius
 
IE 9、Opera 10.5、Safari 5、Chrome 4和Firefox 4，都支持border-radius属性。早期版本的Safari和Chrome，支持-webkit-border-radius属性，早期版本的Firefox支持-moz-border-radius属性。
 
一般这么写：
 
-moz-border-radius: 15px;
border-radius: 15px;
 
注意border-radius必须放在最后声明，否则可能会失效。
 
建议：不要考虑兼容IE圆角，现在大多网站根本不管IE的css3属性，牺牲小部分用户的部分体验，满足大部分用户才是明智之举。如果非要这么做，自行百度。
 