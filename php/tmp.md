
#### 常量

 
函数之外声明的全局变量，在函数内使用还要声明。
 
常量是默认全局的，即使写在函数里面（当然，前提是函数有执行到）。
 
数字型字符串和整形变量使用起来没区别。。。
 
echo '6' + '1' + 1;
输出8
 
echo '100' == 100;
输出1，即表达式为真
 
还有其他方面的，数组下标、case语句等等
 
PHP在比较时能自动将字符串“按照人的理解方式”进行转换
 
 
 
三大数据类型：基本数据类型、复合数据类型（数组、对象）和特殊数据类型（null和resource）
 
全等（===）：类型相同且值相等
 
php的数组本身就是动态数组（键值对），没有指定键的值，它的键按数字递增（从0开始）。
 
和javascript一样的&amp;&amp;语法：test() &amp;&amp; test2();
 
强悍的break n 语法，管他几重循环，照样跳出来。
 
 
奇葩的语法case $number &gt; 7: ，这种语法是好是坏，我不清楚。。。
 
赋值后会把前面的值和类型替换
 
函数是否存在：
 
bool function_exists ( string $functionname )
 
 
empty()函数是用来测试变量是否已经配置。若变量已存在、非空字符串或者非零，则返回 false 值；反之返回 true值。
 
不要用empty()函数来判断字符串是否为空
 
## include和require区别
 
require是无条件包含。这个函数通常放在 PHP 程序的最前面，PHP 程序在执行前，就会先读入 require 所指定引入的文件，使它变成 PHP 程序网页的一部份。常用的函数，亦可以这个方法将它引入网页中。
 
include这个函数一般是放在流程控制的处理部分中。PHP 程序网页在读到 include 的文件时，才将它读进来。这种方式，可以把程序执行时的流程简单化。
 
他们两个的用途是完全一样的，不一定非得哪个放在最前面哪个放在中间。他们最根本的区别在于错误处理的方式不一样。
 
require一个文件存在错误的话，那么程序就会中断执行了，并显示致命错误
include一个文件存在错误的话，那么程序不会中端，而是继续执行，并显示一个警告错误。
 
**以下为补充：** 
 
1. include有返回值，而require没有。
 
2. include()包括并运行指定文件 在处理失败时include() 产生一个警告,被导入的程序代码都会被执行，而且这些程序在执行的时候会拥有和源文件中呼叫到include()语句的位置相同的变量范围。你可以导入同一个服务器中的静态页面。
 
3. include_once()的作用和include()是几乎相同的，唯一的差别在于include_once()会先检查要导入的档案是不是已经在该程序中的其它地方被导入过了，如果有的话就不会再次重复导入（这项功能有时候是很重要的，比方说要导入的里面宣告了一些你自行定义好的函数，那么如果在同一个程序重复导入这个文件，在第二次导入的时候便会发生错误讯息，因为PHP不允许相同名称的函数被重复宣告第二次）。
 
4. require()会将目标文件的内容读入，并且把自己本身代换成这些读入的内容 在处理失败时require() 则导致一个致命错。
这个读入并且代换的动作是在PHP引擎编译你的程序代码的时候发生的，而不是发生在PHP引擎开始执行编译好的程序代码的时候（PHP 3.0引擎的工作方式是编译一行执行一行，但是到了PHP 4.0以后就有所改变了，PHP 4.0是先把整个程序代码全部编译完成后，再将这些编译好的程序代码一次执行完毕，在编译的过程中不会执行任何程序代码）。require()通常来导入静态的内容，而include()则适合用导入动态的程序代码。
 
5. 如同include_once()，require_once()会先检查目标文件的内容是不是在之前就已经导入过了，如果是的话，便不会再次重复导入同样的内容。
 
## 函数做参数
```javascript
$function = "functionName";
$function();
 
$foo = new Foo();
$funcname = "functionName";
$foo-&gt;$funcname();
```

## 其他
我考虑到用Zend Guard Loader组件有些人服务器不能装，我也就没Zend6加密了，只是简单的混淆了下，结果却

## 感悟

 
## 相关文章推荐
 
[php能把函数名作为参数传递吗？](http://www.yunxiu.org/wenda/26/php%E8%83%BD%E6%8A%8A%E5%87%BD%E6%95%B0%E5%90%8D%E4%BD%9C%E4%B8%BA%E5%8F%82%E6%95%B0%E4%BC%A0%E9%80%92%E5%90%97%EF%BC%9F)


1、选择安装Smarty的目录
 
　　如果拥有服务器权限，考虑到安全性可以选择将Smarty安装在WEB程序文档目录之外的地方，然后通过将Smarty安
 
装目录地址包含在PHP.INI文件中的include_path选项。
 
　　如果是虚拟主机权限，或者好几个项目，可以将Smarty安装在各自的项目目录中，在require Smarty类文件，也
 
可以使用Smarty模板引擎。当然为了安全考虑，你可以通过apache禁止相关目录访问。
 
　　另外这两种Smarty安装方式在移植性方面有所区别，第一种方式需要保证每台服务器有相同的Smarty配置，第二
 
种方式对每台服务器配置没有影响。你可以根据各自的需要选择Smarty的安装方式。



1. 类文件都是以“.class.php“为后缀，且类文件名只允许字母，使用驼峰法命名，并且首字母大写，例如：DbMysql.class.php 。
2. 配置和函数等其他类库文件之外的文件一般是分别以“.inc.php“和”.php“为后缀，且文件名命名使用小写字母和下划线的方式，多个单词之间以下 划线分隔，例如config.inc.php ， common.php，install_function.php 。
3. 确保文件的命名和调用大小写一致，是由于在类Unix系统上面，对大小写是敏感的。
4. 类名和文件名一致（包括上面说的大小写一致），且类名只允许字母，例如 UserAction类的文件命名是UserAction.class.php， InfoModel类的文件名是InfoModel.class.php 。




7. 每个 php 文件只允许声明一个类。在类文件里面写其它代码是允许的，但并不鼓励这样做。

8. 任何类变量的声明都必须放在类顶部，先于任何函数的声明。

10. 方法必须总是用 private，protected 或者 public 来声明其作用域。





16. 鼓励尽量使用类型提示，特别是在模块设计中。例如：
class Foo
{
    public function foo(SomeInterface $object)

   {
    }
    public function bar(array $options)
    {
    }
}




LAMP（Linux+Apache+Mysql/MariaDB+Perl/PHP/Python）是一组常用来搭建动态网站或者服务器的开源软件。

一、利用yum安装php，几秒钟搞定！
yum install -y php


Q: apache无法访问
A: 
0.iptables -I INPUT -p TCP --dport 80 -j ACCEPT
1 检测80端口是否开启 netstat -l
2 检测httpd是否提供服务 curl http://127.0.0.1

二、配置Apache，使其支持php。

编辑httpd.conf 文件（我是通过yum安装Apache的，配置文件在/etc/httpd/conf/httpd.conf）

找到 AddType application/x-gzip .gz .tgz 在其下添加如下内容

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

三、完成

php配置已经完成，你可以到Apache的默认发布目录/var/www/html下新建test.php，写个hello world测试一下。





Linux下部署wordpress

下载安装包，解压到/var/www/html目录

在浏览器打开对应的目录

遇到以下错误：

您的PHP似乎没有安装运行WordPress所必需的MySQL扩展。

解决方法：

根据网上方法，

#vi /etc/php.ini

加入：
extension=php_mysql.dll
extension=php_mysqli.dll
结果：还是不行

后来发现是安装php组件php-mysql的原因

执行yum -y install php-mysql

报错：

transaction check error:
...
...
error summary

解决：是软件包版本冲突造成的
然后不顾后果地卸载掉冲突的package包：
rpm -q MySQL-server-advanced --qf '%{NAME} %{VERSION} %{ARCH}'
rpm -e MySQL-server-advanced
重启httpd服务

浏览器刷新一下
成功！

在浏览器的wordpress安装界面输入相关配置，点击下一步，悲剧了。。。

建立数据库连接时出错

肯定是刚才卸载了MySQL-server-advanced的原因，试着连接数据库：

Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock'

心好累。

未完，待续。。。/(ㄒoㄒ)/~~





其他
apache的默认发布目录是：/var/www/html，默认的发布文件是那个目录地下的index.html.

/etc/httpd/conf.d/php.conf

/etc/httpd/conf.d/welcome.conf.












http://archive.apache.org/dist/httpd/binaries/win32/

# configure php
LoadModule php5_module "G:/install/php/php5apache2_4.dll"
PHPIniDir "G:/install/php"
AddType application/x-httpd-php .php .html .htm

环境变量PATH
G:\install\php;G:\install\php\ext;

extension_dir = "G:/install/php/ext"

httpd -e debug



php5.5，只能搭配2.4版本以上的apache，如果你用的是主流的2.2版本或其他，敬请升级到2.4版本


二、配置MySql
在php.ini修改以下配置：

#修改php的扩展库目录为你的实际路径
extension_dir = "D:/Software/GreenSoft/Php/php5.4.6/ext"

#去掉 #extension=php_mysql.dll前面的#号
extension=php_mysql.dll




首先要确保php.ini中extension_dir = "./ext",该设置是php引用dll的目录；
1.将php文件夹下libmysql.dll和php5ts.dll两个文件拷贝至windows目录下的system32下；或者在环境变量中增加D:php;D:phpext。这两个目录是php的安装目录和扩展dll的目录。
2.修改windows安装目录下的php.ini 去掉;extension=php_mysql.dll前面的分号；
3.extension_dir = "d:phpext (文件在PHP.INI中)。