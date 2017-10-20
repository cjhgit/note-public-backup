
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



---------------配置文件目录：/etc/nginx/conf.d/default.conf-----------------



server  {
        listen  80;
        server_name  develop.liangchuantech.com;
        location  /  {
                root  /usr/local/nginx-app/coolkeke-front;
                try_files  $uri  $uri/  /index.html;
        }
}




正在 Ping centrizen.com [119.23.73.154] 具有 32 字节的数据:
来自 119.23.73.154 的回复: 字节=32 时间=8ms TTL=51
来自 119.23.73.154 的回复: 字节=32 时间=8ms TTL=51
来自 119.23.73.154 的回复: 字节=32 时间=8ms TTL=51
来自 119.23.73.154 的回复: 字节=32 时间=7ms TTL=51

https://opensource.org/licenses/mit-license.php

电商如何运营

自媒体如何运营

