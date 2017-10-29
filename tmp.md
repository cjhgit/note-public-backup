
[首页](/all.md)

# TODO

* matlab
* blockly
* localForage
* 阅读源码
* 下载 VMware虚拟机
* 语法糖（Syntactic sugar）
* DSL
* Python range
* 图灵完备
* Source map
* BNF 范示
* java rx
* 离散数学
* markdown + wiki
* WebAssembly
* 值类型、引用类型
* 离线应用 manifest
* 惰性函数
* 安装谷歌浏览器
* for...else
* while else
* 装饰器
* Docker
* 3D 建模

苹果天线门

> 其实我从苹果天线门事件时候就想不通，金属外壳的话，直接拿外壳当天线不就得了

句子迷

其次，在睡觉前大量用脑，会让你的脑袋又紧张又疲劳，会影响你的睡眠质量。

脱口秀：

* 晓松奇谈
* 奇葩说

中水系统

自闭症

（大雾）

信息与安全：

* 个人层面
* 国家层面

* 知乎维权骑士
* 版权印
* 其他维权网站

音乐、影视的版权在国内的变化。
专利
大公司与专利
侵权 国内外

小米远程文件管理（ftp）

辩论

Cardboard

花生壳：一个动态域名解析软件

内网IP有3种：第一种10.0.0.0～10.255.255.255，第二种172.16.0.0～172.31.255.255，第三种192.168.0.0～192.168.255.255

1. 数学课 (概率，统计，微积分等等）
2. 语言课（java，c++）
3. 数据结构和算法
4. 计算机网络
5. 操作系统和编译原理

sudo apt-get install package=version=version

apt-get update
apt-get install openjdk-7-jdk

Comet：基于 HTTP 长连接的“服务器推”技术

sudo apt-get update
sudo apt-get install 

RDC的环境中只安装了python3.5，你可以使用“sudo apt-get update && sudo apt-get install ”来安装不同的版本

默认的构建命令，你们可以参照下npm --python=/usr/alibaba/install/python-3.5.0/bin/python3 --registry=https://registry.npm.taobao.org install --production

修改为自己安装的版本

[INFO] export PATH='.:/usr/alibaba/install/python-3.5.0/bin/python3:/usr/alibaba/install/python-3.5.0/bin/python3/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin'
[INFO] export SCRIPT_ROOT_PATH='/home/admin/16_20170930095105093_25471950_code/cmd'
[INFO] export BASELINE_JDK='java7u52'
[INFO] export PACKAGE_TYPE='app'
[INFO] export PYTHON='/usr/alibaba/install/python-3.5.0/bin/python3'

gyp verb check python checking for Python executable "/usr/alibaba/install/python-3.5.0/bin/python3" in the PATH
gyp verb `which` succeeded /usr/alibaba/install/python-3.5.0/bin/python3 /usr/alibaba/install/python-3.5.0/bin/python3
gyp verb check python version `/usr/alibaba/install/python-3.5.0/bin/python3 -c "import platform; print(platform.python_version());"` returned: "3.5.0\n"
gyp ERR! configure error
gyp ERR! stack Error: Python executable "/usr/alibaba/install/python-3.5.0/bin/python3" is v3.5.0, which is not supported by gyp.
gyp ERR! stack You can pass the --python switch to point to Python >= v2.5.0 & < 3.0.0.
gyp ERR! stack at PythonFinder.failPythonVersion (/home/admin/16_20170930095105093_25471950_code/home-front/node_modules/node-gyp/lib/configure.js:492:19)
gyp ERR! stack at PythonFinder. (/home/admin/16_20170930095105093_25471950_code/home-front/node_modules/node-gyp/lib/configure.js:474:14)
gyp ERR! stack at ChildProcess.exithandler (child_process.js:262:7)

gyp：

特别之处

在已经有很多的构建系统的情况下，gyp诞生的哲学或者说优点如下：

各平台使用各自主流的构建系统。
程序员更熟悉自己的平台，减少学习成本。
构建速度快。自己平台的主流构建系统的速度是各平台优化过的。
在一个平台上可以生成所有支持的平台的工程文件。
如在mac上也可以生成Visual Studio工程，windows上也可以生成Xcode工程。
生成的工程文件和手工创建的工程文件没有区别
这样，随时可以停止使用gyp。别人可以只使用相关工程文件而不使用gyp

vue 多页面应用

https://github.com/creationix/nvm

小娜

npm WARN deprecated gulp-minify-css@1.2.4: Please use gulp-clean-css
npm WARN deprecated express@2.5.11: express 2.x series is deprecated
npm WARN deprecated connect@1.9.2: connect 1.x series is deprecated
npm WARN deprecated minimatch@2.0.10: Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue
npm WARN deprecated minimatch@0.2.14: Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue
npm WARN deprecated graceful-fs@1.2.3: graceful-fs v3.0.0 and before will fail on node releases >= v7.0. Please update to graceful-fs@^4.0.0 as soon as possible. Use 'npm ls graceful-fs' to find it in the tree.
npm WARN deprecated node-uuid@1.4.8: Use uuid module instead
npm WARN deprecated lodash@1.0.2: lodash@<3.0.0 is no longer maintained. Upgrade to lodash@^4.0.0.
npm WARN prefer global node-gyp@3.6.2 should be installed with -g

安装node版本管理工具之NVM

电梯算法

MVC

百度指数

leancloud

> 比如写好的代码放到Server上，虽然只要能跑就算是部署成功了，但公认的最佳实践是使用virtualenv隔离Python环境，这样可以减少以后很多的麻烦，那就值得多花时间去了解，去应用；使用Fabric配合Git进行自动化部署可以大大提高效率，那就也值得花时间去学怎么用。

> 在能够独自写出一个iPhone App并把它放到App Store上之后

> 或是用Rabbit Mq和Celery来做异步队列，可以改善同步执行耗时较久的任务给用户带来的不爽感

项目管理

翻墙：

* [蓝灯（Lantern）](https://github.com/getlantern/forum)
	* 下载，默认安装即可使用。
	
* SS（Shadowsocks）

flash fish
http://www.cnblogs.com/liruihua/p/5957393.html

走出舒适区

《梦的解析》（德语：Die Traumdeutung 英文：The Interpretation of Dreams），是奥地利心理学家西格蒙得·弗洛伊德创作的心理学理论著作，又译做《解梦》。

小兔笔记
https://github.com/TooNote/TooNote

程序员思维

站在巨人的肩膀上

https://www.apple.com/cn/iphone-x/

人性的弱点

在李善友教授看来，他相信世界上存在数量稀少但足可信赖的“第一性原理”，它们像数学公理一样，应该构成我们理解世界的基本起点。

alloydesigner

蚊子

保存聊天记录

辩论：逻辑，价值，口才

说服的艺术

整理文件：

Cordova


https://github.com/kezzbracey/postcss-bem

@component-namespace mint {
    @component actionsheet {
      position: fixed;
      background: #e0e0e0;
      width: 100%;
      text-align: center;
      bottom: 0;
      left: 50%;
      transform: translate3d(-50%, 0, 0);
      backface-visibility: hidden;
      transition: transform .3s ease-out;


vi /etc/nginx/nginx.conf

mkdir /etc/nginx/vhost



/usr/sbin/nginx -s reload

service nginx restart




include /etc/nginx/vhost/*;

# vi /etc/nginx/vhost/jianan-front


server {
    listen 80;
    server_name canalifecare.com;
	location / {
 		proxy_pass http://localhost:9983;
	}
}


/usr/sbin/nginx -c /etc/nginx/nginx.conf

/usr/sbin/nginx-----------文件

重启指令：./nginx  -s  reload  

/usr/sbin/nginx -s reload

---------------配置文件目录：/etc/nginx/conf.d/default.conf-----------------



server  {
        listen  80;
        server_name  develop.liangchuantech.com;
        location  /  {
                root  /usr/local/nginx-app/coolkeke-front;
                try_files  $uri  $uri/  /index.html;
        }
}



ISO的封闭与安卓开放

电商如何运营

自媒体如何运营


迦南
vi /etc/nginx/conf.d/default.conf


==========================================nginx配置===================================/etc/nginx/
https://router.vuejs.org/zh-cn/essentials/history-mode.html----location  /  {
    try_files  $uri  $uri/  /index.html;
}



设计图有色差




Access-Control-Allow-Credentials  true




table-cell垂直居中
缺点;影响position:a
float 也会影响
margin-right 不起作用
.cell {
  display: table-cell;
  vertical-align: middle;
  text-align: center;
  width: 240px;
  height: 180px;
  border:1px solid #666;
  }


 display: table-cell;
            width: 1%;
            能实现水平居中？



网页字体调研

楷体能在什么系统的什么浏览器上面显示


https://segmentfault.com/a/1190000006110417

字体子集

通过Trello建立你的清单管理系统

北京警方发布通告：十九大期间北京地区禁飞无人机等12类航空器

> “低慢小”航空器是指飞行高度在1000米以下、飞行时速小于200公里、雷达反射面积小于2平方米的航空器具。主要包括轻型和超轻型飞机（含轻型和超轻型直升机）、滑翔机、三角翼、动力三角翼、载人气球（热气球）、飞艇、滑翔伞、动力滑翔伞、无人机、航空模型、无人驾驶自由气球、系留气球等12类。

公司

公司类型

什么是公司

如何开公司

在线算盘（Flash）
http://www.guaiguai.com/flash/2940/play.html

群众的眼睛是雪亮的？


## 支付

支付宝
微信支付
PayPal
银行卡
visa
第三方支持
第三方支持整合平台

从地域上来说，银联是中国的卡组织，VISA和万事达都是美国的卡组织。目前国内的银行卡按照打头数字的不同分别归属不同银行卡组织，以“4”字打头的银行卡属于VISA卡组织，以“5”字打头的属于万事达，以“62”、“60”、“9”打头的属于中国银联，而“62”、“60”打头的银联卡是符合国际标准的银联标准卡，可以在国外使用，这也是中国银联近年来的主打卡片。　　
　　
      从用途上看，如果只在国内消费，银联就是最好的选择，但如果经常需要到国外消费，一张VISA或万事达就必不可少了。近年来，为了迎合用户的需求，各大银行都推出了双币卡，也就是银联+VISA或银联+万事达，这样用户在国内消费就可以走银联渠道，到了国外就可以走VISA或万事达渠道。
 
　　那么VISA和万事达之间该如何选择呢？
 
　　其实，各个发卡组织的信用卡有各自的优势。VISA和万事达都是历史比较久的发卡组织，在全球都有较大的影响力。其中，VISA在美国、亚洲国家较为通行，而万事达在欧洲的影响力则更大一些。因而，去欧洲的话，带着万事达标识的信用卡可能更为方便，而在美国则可使用VISA信用卡。小伙伴们可以根据自己常去的境外国家进行选择。



http://lbsyun.baidu.com/index.php?title=uri/api/android
http://lbs.amap.com/api/javascript-api/guide/function/callapp

aFarkas/lazysizes

标注
http://www.mamicode.com/info-detail-1992580.html

首页交互
https://www.tencent.com/zh-cn/index.html

## vi 编辑器

复制

VI中的多行删除与复制
法一：
单行删除，：1（待删除行）d
多行删除 ，：1,10d
法二：
光标所在行，dd
光标所在行以下的N行，Nd

## 无人车

随着无人驾驶技术的发展，无人车的普及以及逐渐替代手动驾驶是必然的事。但无人驾驶技术正在发展，仍有一段很长的路要走。

科技发展的一个趋势是，能够机器完成的事，就没必要让人类来完成。毕竟人力的成本比较高，并且人很容易犯错误。

据世界卫生组织统计，每年有 125 万人死于交通事故。在中国，每年有超过 26 万人死于交通事故。

很显然，如果能普及无人驾驶技术，这个死亡人数的数量会大幅度减少。毕竟相对于机器，人是极其不可靠的。人会疲劳驾驶，会醉驾。很多时候开车的时候一分神，就一命呜呼了。

## 无人驾驶的优势以及应用场景

## 人无驾驶的现状

> 中国由于交通事故每年死亡超过10万人，死者大多是年轻人，占全球交通事故死亡人数的五分之一，居世界各国之首。

这是一个链接到谷歌的[^脚注]。

[^脚注]: http://www.google.com

上火
剪藏失败

跑酷
极限运动
手机号要注销
程序员思维
穿衣风格
量化
堆糖

运动目标
时间记录

压腿

睡前不要吃喝
斗地主

养生

推荐阅读《黑天鹅》和《统计数字会撒谎》这类统计学的图书，不似教材那般枯燥，适合工作以后的人阅读，附录中会有简单介绍。

还有一点需要注意，就像书中所说，实际生活中，以理服人常常不如煽动强的以情动人。逻辑通关了也别沾沾自喜，这很可能是你还没女朋友的原因。

比如我们过年放假，我们飞到南半球去过夏天，在海边吹着舒服的海风，

background-size

background-repeat

写日记谁都会
如何幽默的文章
我已经坚持写很多文章，进一步提高
不同阶段目标不同，方法不同

我需要一个怎样的读书APP ，笔记软件

反鸡汤收集

如“卖淫要不要合法化？”“酗酒是难以自控的疾病还是有意为之的恶习？”“乔治·布什在任时是不是一位成功的总统？”带着对这些问题的观点和立场，你在读书和听讲中不断加以印证。
应该废除死刑？
物质占有欲

收集癖

>  收藏癖，也称储物癖（hoarding），又称强迫性储物症、囤积症、科利尔兄弟综合症，患有此病的人害怕扔掉东西，疯狂地储藏物品，是一种心理疾病。

鸡汤 不可行 坚持 道理我都懂，依然过不好一生

@知识点 link：编辑时可以跳转

答题

URI URL
笔记 记细节

信仰与迷信

> 西方也经过一段“前现代”思潮的影响.也就是实证主义,什么事情如果不能实证就不科学.因此西方人“不都信仰上帝”了,或者说有很多人只是接受这样的传统,而不是真正的信仰了.
  进化论的发展就是在这个时期,无神论和“人定胜天”的论调也发展起来
  不过经历了前现代,人们也发现确实有很多事情不是能过用“实证”解决的.而人定胜天,已经造成了很大的破坏（主要是自然环境）进化论却没有想一开始想当然的成为真理,因为中间环节的诸多证据都被证实无效.今天在西方就有两派了.
  所以,你可以理解,西方人,不是一个人.人群中两者都有.
  
西方没有孝的概念

为什么不能吃它们：猪和鸡的一生
http://v.youku.com/v_show/id_XMzE3ODY1NjA=.html?from=s1.8-1-1.2
