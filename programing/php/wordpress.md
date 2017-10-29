# Wordpress

强大的 CMS 洗头。
 
## 不错的插件

多说：在社会化评论方面功能很强大，但同时也面临着信息安全方面的风险。

Wp Cleanup Optimizer Lite Edition：可以用来清理文章修订版本等冗余数据，优化系统。要用到这个插件的时候才开启，使用完后停用。

## 使用Wordpress时应该注意的事项：
 
尽可能少用插件。
 
开发/修改主题时，最大化地保持可移植性，即主题可以被别人使用而不用修改太多的代码。
 
开发/修改主题时，不要修改wordpress本身的代码。
 
开发主题和插件时，最好开启调试模式。

## 遇到的问题

问题：安装wordpress后打开分类页面和标签页面页面出现404错误  
解决方法：网站后台-设置-固定连接改成 自定义结构


// 使用smtp发送邮件
function mail_smtp( $phpmailer ) {
    /*
    $phpmailer->FromName = '氪星人'; // 发件人的名称
    $phpmailer->Host = 'mail.chenjianhang.com'; // SMTP服务器
    $phpmailer->Port = 25; // SMTP端口
    $phpmailer->Username = 'cjh@chenjianhang.com'; // 邮箱账号
    $phpmailer->Password = 'xxx'; // 邮箱密码
    $phpmailer->From = 'cjh@chenjianhang.com'; // 邮箱账号
    $phpmailer->SMTPAuth = true;
    $phpmailer->SMTPSecure = ''; // ssl对应的端口465
    $phpmailer->IsSMTP();
    */
    $phpmailer->FromName = '氪星人'; // 发件人的名称
    $phpmailer->Host = 'smtp.exmail.qq.com'; // SMTP服务器
    $phpmailer->Port = 25; // SMTP端口
    $phpmailer->Username = 'cjh@chenjianhang.com'; // 邮箱账号
    $phpmailer->Password = 'xxx'; // 邮箱密码
    $phpmailer->From = 'cjh@chenjianhang.com'; // 邮箱账号
    $phpmailer->SMTPAuth = true;
    $phpmailer->SMTPSecure = ''; // ssl对应的端口465
    $phpmailer->IsSMTP();
}
/*
if (function_exists('mail')) {
 
}
*/
//add_action('phpmailer_init', 'mail_smtp');







### Linux下部署wordpress
 
下载安装包，解压到/var/www/html目录
 
在浏览器打开对应的目录
 
遇到以下错误：
 
您的PHP似乎没有安装运行WordPress所必需的MySQL扩展。
 
解决方法：
 
根据网上方法，
 
`#vi /etc/php.ini`
 
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
 
<span style="color: #ff0000;">建立数据库连接时出错</span>
 
肯定是刚才卸载了MySQL-server-advanced的原因，试着连接数据库：
 
Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock'
 
心好累
 
未完，待续。。。/(ㄒoㄒ)/~~
 

 