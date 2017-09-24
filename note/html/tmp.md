

### margin-top

父元素与子元素之间的margin-top问题(css hack)
解决方法：
1、修改父元素的高度，增加padding-top样式模拟（padding-top：1px；常用）
2、为父元素添加overflow：hidden；样式即可（完美）
3、为父元素或者子元素声明浮动（float：left；可用）
4、为父元素添加border（border:1px solid transparent可用）


## HTML5
 
###  更好的音视频支持
 
使用&lt;audio&gt;&lt;video&gt;标签，播放音视频和显示图片一样简单。可惜兼容性是致命伤。
 








 

### article
文章内容，通常作为内容页的主体。article 标签 是页面主内容的容器。 页面上可以多 article 。
 

### aside
该标签被包含在article标签中作为主要内容的附属信息部分。
 

### section
代表文档中的“节”或“段”。著作权归作者所有。每一个section都是一个整体，里面可以用独立的header、aside、article、footer。通常在页面中作为板块的划分，也有用作文章（Acticle）的章节。

一个section通常由内容和标题组成，通常不推荐那些没有标题的内容用section，在HTML 5 Outliner这个网站可以检测没有标题的section，section的作用是对页面上的内容进行分块，如各个有标题的版块、功能区或对文章进行分段，不要与有自己完整、独立内容的article混淆。拿报纸举个例子：一份或一张报纸有很多个版块，有头版、国际时事版块、体育版块、娱乐版块、文学版块等等，像这种有版块标题的、内容属于一类的版块就可以用section包起来。然后在各个版块下面，又有很多文章、报道，每篇文章都有自己的文章标题、文章内容。这个时候用article就最好。如果一篇报道太长，分好多段，每段都有自己的小标题，这时候又可以用section把段落包起来。


### 其他
hgroup：代表“网页”或“section”的标题，当元素有多个层级时，该元素可以将`h1`到`h6`元素放在其内。如果只需要一个h1-h6标签就不用hgroup，如果有连续多个h1-h6标签就用hgroup。

h1-h6：文章标题
 

 
lable

此外还有label、address等等，不一一列举了。以后的网页设计中，我会尽量用语义标签。
 



## 未整理
 
section 不是一个专用来做容器的标签，专用的是 divsection 里应该有 标题（h1~6），但文章中推荐用 article 来代替

一个section标签通常由内容及其标题组成。
当一个内容需要被直接定义样式或通过脚本定义行为时，推荐使用div而非section标签。
section标签中的内容可以单独存储到数据库中或输出到word文档中。
<section> 并不是一个容器.<section>元素是有语意的区段，帮助构建文档大纲。它应该包含标题
 
文档、文档、文档、大纲
div、header、nav、footer
section不用、除非在文档类的结构中
