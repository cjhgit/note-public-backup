[TOC]
 
## JQuery
 

jQuery Validation是个不错的验证框架。

 
1、在全部代码前加上文件说明注释
例如：
/*
* @extends jquery.1.7.2
* @fileOverview 搜索提示框
* @author zmc
* @email
* @sitewww.jq-school.com
* @version 0.2
* @date 2012-06-04
* Copyright (c) 2012 ZMC
*/

 
2、函数务必加注释
 
比如以下代码是其中的一个方法setContents：
zmc.tips.prototype = {
/** *向提示框添加内容 */
setContents : function(content){
    ...........
}}
3、参数务必加注释
 
例如：
//默认参数
$.fn.tips.defaults = {
/**目标容器*/
applyTo : null,
/**内容*/
content : "",
/**搜索框的位置*/
position : "topMiddle",
/**搜索框位置偏移*/
offest : {"left":0,"top":0},
/**提示框颜色*
/ color : "blue"
}
 
 


三、jquery插件开发的一些建议
 
1、请多使用data()方法 jquery中data()方法非常有用，尤其在jquery插件开发中，因为data()所创建的缓存，可以完整的保存各种数据类型的数据，这是其他缓存机制无法比拟的。
2、请使用bind来绑定事件 很多朋友喜欢以下的代码：
$(".yitip").click(function(){ ........ })
但在jquery插件开发中更提倡使用bind：
$(".yitip").bind('click',function(){ ......... })



 
a) 尽量使用Id选择器
 
b) 样式选择器应该尽量明确指定tagName, 如果开发人员使用样式选择器来获取dom，且这些dom属于同一类型，例如获取所有className为jquery的div，那么我们应该使用的写法 是$('div.jquery')而不是$('.jquery')，这样写的好处非常明显，在获取dom时jQuery会获取div然后进行筛选，而不是 获取所有dom再筛选。
 
c) 避免迭代，很多同学在使用jQuery获取指定上下文中的dom时喜欢使用迭代方式，如$('.jquery .child')，获取className为jquery的dom下的所有className为child的节点，其实这样编写代码付出的代价是非常大 的，jQuery会不断的进行深层遍历来获取需要的元素，即使确实需要，我们也应该使用诸如$(selector,context), $('selector1>selector2'), $(selector1).children(selector2), $(selctor1).find(selector2)之类的方式。




3、使用裸协议的URL（去掉http:或者https:），如上面代码展示的那样，我在之前的文章中也提到过，加载CDN可以省掉http,见文章：http://www.haorooms.com/post/web_qd_html_leng





关于选择器



4.多级查找中，右边尽量指定得详细点而左边则尽量简单点。了解更多

// 丑陋
$("div.data .gonzalez");// 优化后
$(".data td.gonzalez");
5.避免冗余。详情或者查看性能比较

$(".data table.attendees td.gonzalez");// 好的方式：去掉了中间的冗余
$(".data td.gonzalez");
6.指定选择的上下文。

// 劣质的代码：因为需要遍历整个DOM来找到.class
$('.class');// 高品代码：因为只需在指定容器范围内进行查找
$('.class', '#class-container');
7.避免使用万能选择器。查看具体阐释

$('div.container > *'); // 差
$('div.container').children(); // 棒
8.警惕隐式的万能选择器。省略的情况下其实使用的就是*号通配符。更多信息

$('div.someclass :radio'); // 差
$('div.someclass input:radio'); // 棒
9.ID已经表示唯一了，背后使用的是document.getElementById()，所以不要和其他选择器混淆了。

$('#outer #inner'); // 脏
$('div#inner'); // 乱
$('.outer-container #inner'); // 差
$('#inner'); // 干净利落，后台只需调用document.getElementById()
DOM操作

1.操作任何元素前先将其从文档卸载，然后再贴回去。请看

var $myList = $("#list-container > ul").detach();//...a lot of complicated things on $myList
$myList.appendTo("#list-container");


3、不要用缺失的元素，具体请看

// BAD: This runs three functions before it realizes there's nothing in the selection
$("#nosuchthing").slideUp();// GOODvar $mySelection = $("#nosuchthing");if ($mySelection.length) {
    $mySelection.slideUp();}
事件

1.一个页面只写一个文档ready事件的处理程序。这样代码既清晰好调试，又容易跟踪代码的进程。







6.如果可能尽量在绑定事件处理程序时使用一个命名空间，这样可以方便地取消绑定而不会影响其他绑定。

$("#myLink").on("click.mySpecialClick", myEventHandler); // 不错// 之后，让我们优雅地解除绑定
$("#myLink").unbind("click.mySpecialClick");
7.当选择某个元素的子元素的时候，尽量在后面选择，不要在前面选择其中选择。如下：

$("#list a").on("click", myClickHandler); // BAD, you are attaching an event to all the links under the list.
$("#list").on("click", "a", myClickHandler); // GOOD, only one event handler is attached to the parent.
Ajax异步操作

1.不要用.getJson() 或 .get(),直接用直接用$.ajax() ，因为jQuery内部还是将前者转化为$.ajax()

2.表对HTTPS站点使用HTTP去发起请求，最好干脆就表指定（将HTTP或者HTTPS从你的URL中移除）



4.尽量指明数据类型以便你自己清楚要处理什么样的数据（见下方会提到的Ajax模板）

5.对于异步动态加载的内容，最好使用代理来绑定事件处理程序。这样的好处是对于之后动态加载的元素事件同样有效。了解更多

$("#parent-container").on("click", "a", delegatedClickHandlerForAjax);
6.使用Promise模式。更多例子

$.ajax({ ... }).then(successHandler, failureHandler);// 抑或var jqxhr = $.ajax({ ... });
jqxhr.done(successHandler);
jqxhr.fail(failureHandler);
7.标准的Ajax模板如下，查看官方案例

var jqxhr = $.ajax({
    url: url,
    type: "GET", // 默认为GET,你可以根据需要更改
    cache: true, // 默认为true,但对于script,jsonp类型为false,可以自行设置
    data: {}, // 将请求参数放这里.
    dataType: "json", // 指定想要的数据类型
    jsonp: "callback", // 指定回调处理JSONP类型的请求
    statusCode: { // 如果你想处理各状态的错误的话404: handler404,500: handler500
    }});
jqxhr.done(successHandler);
jqxhr.fail(failureHandler);
动画与特效

1.保持一个始终如一风格统一的动画实现

2.紧遵用户体验，不要滥用动画特效

使用简洁的显示隐藏，状态切换，滑入滑出等效果来展示元素
使用预设值来设置动画的速度'fast'，'slow'，或者400（中等速度）
插件相关

1.始终选择一个有良好支持，文档完善，全面测试过并且社区活跃的插件



链式结构

1.除了用变量将jQuery选择器返回的结果保存，还可以利用好链式调用。

$("#myDiv").addClass("error").show();
2.当链式调用多达3次以上或代码因绑定回调略显复杂时，使用换行和适当的缩进来提高代码的可读性。

$("#myLink").addClass("bold").on("click", myClickHandler).on("mouseover", myMouseOverHandler).show();
3.对于特别长的调用最好还是用变量保存下中间结果来简化代码。
