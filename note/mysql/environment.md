# 环境

## Windows

## Linux下的MySQL安装
 
### RPM方式安装（推荐）
 
一、安装前先把MySQL和Mariadb卸载干净。
 (rpm -e --nodeps mariadb-libs-5.5.37-1.el7_0.x86_64)
二、下载三个rpm包，如：
 
MySQL-client-advanced-5.6.22-1.el7.x86_64.rpm
MySQL-devel-advanced-5.6.22-1.el7.x86_64.rpm
MySQL-server-advanced-5.6.22-1.el7.x86_64.rpm(这一步成功后会有一大段明显的文字:***mysql.com***)
 
三、安装这三个rpm包。
 
四、启动MySQL
 
service mysqld start
chkconfig --list | grep mysqld 
chkconfig mysqld on

may need:

# yum install libaio
# yum install perl

 Q: please install the following Perl modules before executing /usr/bin/mysql_install_db:
A: yum install -y perl-Module-Install.noarch


### yum方式安装（安装失败，不要看）
 
一、安装配置MySQL的yum源
 
要使用yum 安装mysql，要使用mysql的yum仓库，先从官网下载适合你系统的仓库
[http://dev.mysql.com/downloads/repo/yum/](http://dev.mysql.com/downloads/repo/yum/)
centos 6.5 对应的是mysql-community-release-el6-5.noarch.rpm
```
#wget http://dev.mysql.com/get/mysql57-community-release-el7-7.noarch.rpm
#yum localinstall mysql-community-release-el7-7.noarch.rpm
# yum repolist all | grep mysql
# yum-config-manager --disable mysql55-community
# yum-config-manager --disable mysql56-community
# yum-config-manager --enable mysql57-community-dmr
# yum repolist enabled | grep mysql
 
```
 
### 编译方式安装（不推荐）
 
极其不建议用这种方式安装，不知道为什么网上很多人这么做，坑。
 
 
MySQL5.5开始弃用了常规的configure编译方法，采用cmake编译。
MySQL5.7编译cmake要求版本最低为2.8
编译MySQL5.7以及更高的版本时，需要下载并引用或者直接安装boost库
从MySQL 5.7.5开始Boost库是必需的，不同版本的MySQL对boost的版本要求也不一样，且版本要求很严格，太新
太旧都不行。
MySQL5.7.7rc--boost 1.57.0
MySQL 5.7.10--boost 1.59.0
boost版本错误cmake时会有错误提示。
 
一、安装CMake编译器、Boost库、ncurses库和GNU分析器生成器bison这4种工具。
二、下载MySQL源码并解压，进入mysql目录
三、cmake . -DDOWNLOAD_BOOST=1 \
-DWITH_BOOST=/usr/local/boost # 改成你的boost路径
四、make &amp;&amp; make install（漫长的等待）
 
五、不知道（表示1G内存的服务器第四部是不可能成功的，设了虚拟内存还是各种死机）
 
如果make出错后重新运行配置，需要删除CMakeCache.txt文件
 
```
# make clean
# rm -f CMakeCache.txt
```
 
 
错误：
 
does not appear to contain CMakeLists.txt
 
解决：
 
http://dev.mysql.com/downloads/mysql/官网下载，注意Select Platform选择Source Code（大概40多M），再点击最后一个链接（Generic Linux。。。）
 
 
 
internal compiler error: Killed (program cc1plus)
 




## Linux下的Mariadb安装
 
Centos7默认数据库不是mysql而是Mariadb（MySQL的一个分支，不再使用MySQL是因为MySQL有闭源的可能性），而Mariadb完全兼容MySQL。
 
yum上面的Mariadb版本太低。
yum install mariadb mariadb-server # 安装Mariadb
systemctl start mariadb # 启动mariadb
systemctl enable mariadb # 开机自启动
mysql_secure_installation # 设置 root密码等相关
mysql -uroot -p123456 # 登录
exit # 退出
 
设置数据库默认的字符集为utf8
vi /etc/my.cnf
写入：
default-character-set = utf8
 
常用命令
show databases
drop database dbname
 
 
 
允许远程访问：
update user set Host ="%" where User = "root";
select Host, User from user;
配置/etc/mysql/my.cnf

## 卸载

```
rpm -qa|grep -i mysql
```
卸载后/var/lib/mysql中的数据及/etc/my.cnf不会删除，如果确定没用后就手工删除
　　rm -f /etc/my.cnf
　　rm -rf /var/lib/MySQL

usr/bin/mysql 是指：mysql的运行路径 
var/lib/mysql 是指：mysql数据库文件的存放路径 
usr/lib/mysql 是指：mysql的安装路径


/etc/init.d/mysql status 


问题：
[root@iZ28gznnhgwZ ~]# service mysqld start
Redirecting to /bin/systemctl start  mysqld.service
Failed to issue method call: Unit mysqld.service failed to load: No such file or directory.
解决：
 /etc/init.d/mysql start

 问题：
 Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock'
 解决：
 mysql 未启动

Q: Starting MySQL.The server quit without updating PID file (/var/lib/mysql/iZj6c4ogunuhbxgxcg4upwZ.pid).[FAILED]
A: 
Can't open and lock privilege tables: Table 'mysql.user' doesn't exist

Q: MySQL is not running, but lock file (/var/lock/subsys/mysql) exists[FAILED]
???
A: rm /var/lock/subsys/mysql 

MySQL is not running[FAILED]


forget root password:

mysqld_safe --skip-grant-tables &

mysql> use mysql;
mysql> UPDATE user SET password=password("test123") WHERE user='root';   
mysql> flush privileges;
mysql> exit;    





## 修改密码

一、拥有原来的myql的root的密码；


方法一：
在mysql系统外，使用mysqladmin
# mysqladmin -u root -p password "test123"
Enter password: 【输入原来的密码】

方法二：
通过登录mysql系统，
# mysql -uroot -p
Enter password: 【输入原来的密码】
mysql>use mysql;
mysql> update user set password=passworD("test") where user='root';
mysql> flush privileges;
mysql> exit;      


二、忘记原来的myql的root的密码；


# mysqld_safe --skip-grant-tables &
&，表示在后台运行，不再后台运行的话，就再打开一个终端咯。
# mysql
mysql> use mysql;
mysql> UPDATE user SET password=password("test123") WHERE user='root';   
mysql> flush privileges;
mysql> exit;                         
##本来mysql是不分大小写的，但是这个是修改的mysql中的mysql数据库的具体的值，要注意到。




## phpmyadmin

### install

在CentOS 7上:

$ sudo yum install phpmyadmin
在CentOS 7上:

$ sudo yum install phpmyadmin php-mcrypt

### config

默认情况下，CentOS 7上的phpMyAdmin只允许从回环地址(127.0.0.1)访问。为了能远程连接，你需要改动它的配置。

用文本编辑器打开phpMyAdmin的配置文件(路径：/etc/httpd/conf.d/phpMyAdmin.conf)，找出并注释掉带有"Require ip XXXX"字样的代码行。会有四处这样的代码行，用"Require all granted"取而代之。重新改动过的配置文件如下所示。


sudo ln -s /usr/share/phpmyadmin /var/www







## Linux


1、查找以前是否装有mysql

命令：rpm -qa|grep -i mysql

2、停止mysql服务、删除之前安装的mysql

删除命令：rpm -e –nodeps 包名
# rpm -ev MySQL-client-5.5.25a-1.rhel5
# rpm -ev MySQL-server-5.5.25a-1.rhel5

3、查找之前老版本mysql的目录、并且删除老版本mysql的文件和库

find / -name mysql
查找结果如下：
[root@localhost ~]# find / -name mysql
/var/lib/mysql
/var/lib/mysql/mysql
/usr/lib64/mysql

删除对应的mysql目录
rm -rf /var/lib/mysql
rm -rf /var/lib/mysql
rm -rf /usr/lib64/mysql
具体的步骤如图：查找目录并删除



注意：卸载后/etc/my.cnf不会删除，需要进行手工删除
 rm -rf /etc/my.cnf

4、再次查找机器是否安装mysql

rpm -qa|grep -i mysql
无结果，说明已经卸载彻底、接下来直接安装mysql即可