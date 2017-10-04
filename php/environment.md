# 环境搭建

## Windows

查看当前 PHP 版本：
php -v


首先，需要在windows下安装好如下环境：

1.apache服务器

2.VC14支持包

如果你的windows下还没有安装好以上两个环境，可以参考本网站的文章：

“如何在windows 7 下安装多个 apache服务”（安装第一个apache也一样原理，重点是端口不冲突就行）

关于vc支持包的说明:

在windows下，不同的php版本和不同的apache版本都需要对应相应的vc支持包，这里你就需要留意你下载的apache和php是什么版本了。下面我给大家列出一个对照表：

VC9：Microsoft Visual C++ 2008

VC11：Microsoft Visual C++ 2012

VC14：Microsoft Visual C++ 2015

这里我安装的apache版本是：httpd-2.4.23-win64-VC14；php版本是：php-7.0.12-Win32-VC14-x64；所以我需要安装的vc支持包是：VC14：Microsoft Visual C++ 2015，

VC14 运行环境下载地址为：https://www.microsoft.com/zh-cn/download/confirmation.aspx?id=48145

好了，搭建好以上两个环境，那么我们就可以开始安装我们的php了，请往下面看：

一、下载php

官方下载地址：http://windows.php.net/download/
下载X64 线程安全版本

将下载的 zip 文件解压到指定目录，比如我将其解压到D:\wamp\php7 ，

然后进在该目录下运行如下命令查看 PHP 版本信息：php -v


如果你的VC环境没有安装（或者版本不对）的话则会弹出如下错误：

```
xxx.dll未安装
```

好了，就是这么简单。下面就开始配置了




设置电脑环境变量中的->系统变量(注:不是用户变量)

新建 phpext   值 E:\AppServ\php56\ext      //扩展路径
新建 PHPRC  值 E:\AppServ\php56         //php路径

Path 增加E:\AppServ\php56         //php路径



二、配置httpd.conf

在你安装的apache目录下找到conf/httpd.conf并打开

1） 添加PHP模块

```
LoadModule php7_module "G:/install/php-7.1.6/php7apache2_4.dll"
```

2） 添加扩展名

```
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```

3） 指定php.ini配置文件路径

在httpd.conf文件里指定PHP配置文件php.ini的目录，这里定位到httpd.conf文件的未尾，在文本最后面一行添加 如下代码：

php.ini-development 复制一份，命名为 php.ini
PHPIniDir "D:/wamp/php7"（这里的“D:/wamp/php7”为你的php.ini文件存放的实际路径）


4） 配置DirectoryIndex

查找“DirectoryIndex”的部分，大概在282行，在DirectoryIndex的后面追加一个“index.php”



与PHP相关的Apache配置已经完成了。

特别提醒：变更Apache的配置文件之后别忘了重启Apache！

三、配置php.ini

首先，将php安装目录下的php.ini-production改名为php.ini

打开php.ini，做如下几个修改：

1） 设置php的扩展路径

查找 extension_dir = "ext" ，把前面的分号去掉
最好配绝对路径，配相对路径有时候就是会加载不到。

2）开启常用的php扩展，如：

extension=php_mbstring.dll（php多字节字符串扩展）

extension=php_mysql.dll（mysql库扩展）

extension=php_mysql.dll（mysqli库扩展）

开启方式：查找以上扩展，把前面的分号（;）删掉就行。

3）设置默认时区

date.timezone = Asia/Shanghai

好了，以上就是关于Windows服务器上安装配置PHP7.0的步骤，下面让我们来测试一下吧

四、测试

在你的apache站点目录下新建一个index.php (当然也可以是别的名字)，

用文本编辑器打开（如记事本），在里面添加以下代码，保存

<?php

phpinfo();

?>

然后在浏览器输入http://localhost/index.php访问，这时你会看到如下页面

添加的path
G:\install\php-7.1.6
G:\install\php-7.1.6\ext



open ssl开启：

先检查一下自己的php文件夹下面有没有libeay32.dll、ssleay32.dll这2个文件。
从windows.php.net下载的php一般都带，但是从www.php.net下载的一般都不带。




没有的话，去http://windows.php.net/downloads/php-sdk/deps/这边下载openssl。
windows.php.net官网给的openssl下载地址会404，所以最好自己手动找。
VC版本要和自己的php一样，不知道的话phpinfo然后看一下Compiler。
下载之后把bin下面的libeay32.dll、ssleay32.dll复制到php文件夹下面。

1。
extension=php_openssl.dll

改php.ini：
1) 启用php_openssl。
extension=php_openssl.dll
 讲php文件夹下的： php_openssl.dll， ssleay32.dll， libeay32.dll 3个文件拷贝到 WINDOWS\system32\  文件夹下。

2) extension如果是第一次启用的话，需要把上面ext根路径配一下。
最好配绝对路径，配相对路径有时候就是会加载不到。
extension_dir = "c:/php5.6/ext"




重启apache使生效。


看看openssl相关方法（比如openssl_x509_parse）是否正常可用。
再可以看看phpinfo和之前什么区别（就是一个有openssl，一个没有啦）。



### WAMP
 
WAMP（Windows+Apache+Mysql/MariaDB+Perl/PHP/Python）。
 
略。

## Linux

LAMP（Linux+Apache+Mysql/MariaDB+Perl/PHP/Python）是一组常用来搭建动态网站或者服务器的开源软件。
 
一、利用yum安装php，几秒钟搞定！
 
二、配置Apache，使其支持php。
 
编辑httpd.conf 文件（我是通过yum安装Apache的，配置文件在/etc/httpd/conf/httpd.conf）
 
找到 AddType application/x-gzip .gz .tgz 在其下添加如下内容
 
AddType application/x-httpd-php .php      (.前面有空格)
 
AddType application/x-httpd-php-source .phps        (.前面有空格)
 
三、完成
 
php配置已经完成，你可以到Apache的默认发布目录/var/www/html下新建test.php，写个hello world测试一下。
 

## cpmposer installation

composer -V