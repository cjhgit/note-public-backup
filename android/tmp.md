[TOC]
 

+创建BaseActivity（做好页面的缓存策略，

别对Bundle savedInstanceState视而不见


## API兼容性

### API极其对应的版本API等级
 
API等级9：Android 2.3 - 2.3.2 Gingerbread
 
API等级10：Android 2.3.3-2.3.7 Gingerbread
 
API等级11：Android 3.0 Honeycomb
 
API等级12：Android 3.1 Honeycomb
 
API等级13：Android 3.2 Honeycomb
 
API等级14：Android 4.0 - 4.0.2 Ice Cream Sandwich
 
API等级15：Android 4.0.3 - 4.0.4 Ice Cream Sandwich
 
API等级16：Android 4.1 Jelly Bean
 
API等级17：Android 4.2 Jelly Bean
 
API等级18：Android 4.3 Jelly Bean
 
API等级19：Android 4.4 KitKat
 
API等级20：Android 4.4W
 
API等级21：Android 5.0 Lollipop
 
API等级22：Android 5.1 Lollipop
 
API等级23：Android 6.0 Marshmallow

##分辨率兼容性

分辨率差异大，只适配主流分辨率
![](file:///F:\Users\cjh1\Desktop\note\学习\Android\image\5f72c29f-1edf-4489-a310-fac1e9447c64.jpg)

数据来源：[友盟统计](http://www.umindex.com/devices/android_resolutions)

其中前五名的屏幕比例（宽：长）
0.5625
0.5625
0.5620
0.6
0.5625


dp和px换算
在Android中，规定以160dpi为基准，1dip=1px，如果密度是320dpi，则1dip=2px，以此类推。


假如同样都是画一条320px的线，在480*800分辨率手机上显示为2/3屏幕宽度，在320*480的手机上则占满了全屏，如果使用dp为单位，在这两种分辨率下，160dp都显示为屏幕一般的长度。这也是为什么在Android开发中，写布局的时候要尽量使用dp而不是px的原因。



名称    屏幕密度
mdpi   160dp
hdpi   240dp
xhdpi   320dp
xxhdpi   480dp
xxxhdpi   640dp


名称    图标尺寸
ldip     32x32px
mdpi   48x48px
hdpi    72x72px
xhdpi    96x96px
xxhdpi    144x144px
xxxhdpi    192x192px


## string.xml
国际化、常量

按照编程规范来说要尽量避免在java代码中出现中文。

执行效率忽略不计。
常量写在Java类里面。
string.xml更多的是为了国际化需要，通常把中文写在里面。不要把它当做定义常量的文件。
比如项目中多次用到的字符串：
final String URL = "https://www.zhihu.com";
你把它写在string.xml里面就不适合了。 


## color.xml


## 资源命名

现在的我的习惯是根据activity来划分string资源，这样哪个界面显示的字符串也就清楚了比如登录activity里的字符放在strings_activity_login.xml
文件中一些全局的资源放在strings.xml
其他资源类似



经过实验，我总结了如下两个方面。首先要使用BitmapFactory.decodeStream解析

图片文件，BitmapFactory.decodeStream直接使用本地方法解析图片文件，无疑会

快很多。其次，对于一个120*120的1K文件来说，使用通常的方法解析，一个点要占

8个字节，也就是120*120*8=115200，这无疑太大了。因此可以设置

BitmapFactory.decodeStream的Options，将options.inPreferredConfig 设置为 

Bitmap.Config.ALPHA_8，这样解析时一个字节只需要占用1个字节，这无疑大大减

少了内存占用。
```
int[] bgResIds = { R.drawable.bg1, R.drawable.bg2, R.drawable.bg3 };
		tableResource = createTableResource2(BACKGROUND, "背景", 

bgResIds);
		tableResources.add(tableResource);

private TableResource createTableResource2(PortraitPart component, String 

title, int[] resourceIds) {
		TableResource tableResource = new TableResource();
		tableResource.setPortraitPart(component);
		tableResource.setTitle(title);
		tableResource.setResourceIds(resourceIds);
		return tableResource;
	}
```



## 其他
 
google提供了Android Support Library package 系列的包来保证来高版本sdk开发的向下兼容性，即我们用4.x开发时，在1.6等版本上，可以使用高版本的有些特性，如fragement,ViewPager等，下面，简单说明下这几个版本间的区别：
 
Android Support v4:  这个包是为了照顾1.6及更高版本而设计的，这个包是使用最广泛的，eclipse新建工程时，都默认带有了。
 
Android Support v7:  这个包是为了考虑照顾2.1及以上版本而设计的，但不包含更低，故如果不考虑1.6,我们可以采用再加上这个包，另外注意，v7是要依赖v4这个包的，即，两个得同时被包含。
 
Android Support v13  :这个包的设计是为了android 3.2及更高版本的，一般我们都不常用，平板开发中能用到。
 
 
libbspatch.so
增量更新

## 应用层的优化
应用层的性能优化通常可以从以下几个方面考虑：
1. 了解编程语言的编译原理，使用高效编码方式从语法上提高程序性能；
2. 采用合理的数据结构和算法提高程序性能，这往往是决定程序性能的关键；
3. 重视界面布局优化；
4. 采用多线程、缓存数据、延迟加载、提前加载等手段，解决严重的性能瓶颈；
5. 合理配置虚拟机堆内存使用上限和使用率，减少垃圾回收频率；
6. 合理使用native代码；
7. 合理配置数据库缓存类型和优化SQL语句加快读取速度，使用事务加快写入速度；
7. 使用工具分析性能问题，找出性能瓶颈；













 
3. 熟悉Android系统架构及相关技术，1年以上实际Android平台开发经验；有过1~2款产品经验；
 
4.熟悉Android开发架构和API调用；
 
5.熟悉面向对象编程，图形界面开发；
 
6. 熟练掌握Android界面布局及绘制、数据存储、网络通信机制等；


 
2、两年以上的Java开发经验， 深刻理解面向对象设计和开发思想；
 
3、熟悉Socket编程、TCP/IP模型、异步网络模块者优先； 
 
4、良好的沟通能力与团队协作能力


4.熟悉Android开发架构和API调用；
 
5.熟悉面向对象编程，图形界面开发；
 
6. 熟练掌握Android界面布局及绘制、数据存储、网络通信机制等；
 

 
2、两年以上的Java开发经验， 深刻理解面向对象设计和开发思想；
 
3、熟悉Socket编程、TCP/IP模型、异步网络模块者优先； 
 
4、良好的沟通能力与团队协作能力，高度的工作责任心和敬业精神。
 
2、熟悉Android开发平台及框架原理，能独立进行Android应用程序开发；
 
3、精通Android的基本组件使用，熟练使用Android各种布局与控件，熟练使用各种动画，熟悉Sqlite；
  
5、对APP性能调优以及多分辨率适配有一定的开发经验；
 
6、对Android各类开源库有一定的了解，并在开发中实践；
 
7、喜欢钻研技术，强烈的责任心和上进心，良好的团队沟通和合作能力。
 
3. 熟悉Android系统架构及相关技术，
 
4.熟悉Android开发架构和API调用；
 
5.熟悉面向对象编程，图形界面开发；
 
6. 熟练掌握Android界面布局及绘制、数据存储、网络通信机制等；
 

另外如果简历里附带了博客链接，GitHub地址，相关作品的，可以提前去看看，直接看人家多年积累的文章与代码，比这短短一小时的面试来得靠谱的多。

 Android经验</b><br>如果不是校招，Android经验是必须的，我比较喜欢问一些基础概念与技术原理，比如Activity、View、Window的理解，各LaunchMode的使用场景，View的绘制流程，Touch事件机制，Android动画的原理，Handler, Looper的理解，Android跨进程通讯的方式，Binder的理解，Android Mashup设计的理解等等。

<br><br><b>2. Java水平</b><br>基本上就是Effective Java那本书里提到的东西，如果你背完那本书里的问题，并且对答如流，没问题，就要你这样的。其实也会考察关于final用法，反射原理，注解原理，java编译过程，GC等一些常见问题。 <br><br><b>


《Clean Code

