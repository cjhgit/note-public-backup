
## Shell命令
 
### 查看系统信息
 
getconf LONG_BIT # 获得机器字长
 
cat /etc/redhat-release # 查看系统版本
 
[Linux上的free命令详解](http://www.cnblogs.com/coldplayerest/archive/2010/02/20/1669949.html)
 
### service
 
service servicename status
 
## yum
 
问题：所有的yum命令都失效了，错误提示：Error: File contains no section headers.
file: file://XXX.repo, line: 1

原因：
 
XXX.repo文件格式错误，你可以在/etc/yum.repos.d文件夹下找到其他repo文件，仿照上面的格式，把出错的文件改成正确的格式。
 

 
 
## 进程机制
 
fork被调用一次，却能够“返回两次”，在父进程中返回新创建子进程的进程ID，在子进程中返回0。
 
理解这个例子就理解了进程的创建机制：[从一道面试题谈linux下fork的运行机制](http://www.cnblogs.com/leoo2sk/archive/2009/12/11/talk-about-fork-in-linux.html)
 
## Linux下的C编程
 
gcc
 
-c表示仅将源码编译成为目标文件，并不制作链接等功能
 
-O 为产生最佳化的参数
 
-Wall 为产生更详细的编译过程信息
 
gcc sin.c -lm -L/lib -L/usr/lib
 
-I/include
 
### makefile
 
规则
 
目标 ： 需要的条件 （注意冒号两边有空格）
 
命令　　（注意前面用tab键开头）
 
定义变量objects
 
objects = main.o kbd.o command.o
 
使用变量：${objects}
 

 
通配符
 
可以看看这篇文章，写得很详细：
 
[跟我一起写 Makefile](http://blog.csdn.net/ruglcc/article/details/7814546)
 
## 其他
 
RHEL（Red Hat Enterprise Linux）不是免费的。
 
CentOS（Community ENTerprise Operating System）
 
DNS服务 named
 
[Linux启动过程详解](http://blog.chinaunix.net/uid-26495963-id-3066282.html)
 
[/etc/inittab文件分析](http://www.cnblogs.com/sdphome/archive/2011/10/25/2224585.html)
 
[linux文件系统简介](http://www.cnblogs.com/yyyyy5101/articles/1901842.html)
 
[Linux分区命名将更加清晰详细](http://os.51cto.com/art/201002/183095.htm)
 
[理解 Linux 的硬链接与软链接](http://www.ibm.com/developerworks/cn/linux/l-cn-hardandsymb-links/)



## Java
yum -y install java-1.8.0-openjdk*

## cmake

1. 安装gcc等必备程序包
yum install -y gcc gcc-c++ make automake

2. 下载安装包、解压、进入目录
下载地址：https://cmake.org/files/v3.4/cmake-3.4.1.tar.gz

3. 安装[默认安装路径是/usr/local/bin]

./bootstrap
gmake

gmake install

六、完成

cmake -version # 查看是否安装成功

【Ncurses】提供功能键定义(快捷键),屏幕绘制以及基于文本终端的图形互动功能的动态库。
yum -y install ncurses-devel

【bison】GNU分析器生成器
wget -c http://git.typecodes.com/libs/ccpp/bison-3.0.tar.gz
tar -zxf bison-3.0.tar.gz &amp;&amp; cd bison-3.0/ &amp;&amp; ./configure
make &amp;&amp; make install
cd ~ &amp;&amp; rm -rf bison-3.0*

【Boost库】一个开源可移植的C++库，是C++标准化进程的开发引擎之一
下载地址：
http://sourceforge.net/projects/boost/files/boost/
下载后解压，不用安装，记住解压后的路径


## Apache
yum install httpd -y
chkconfig --level 35 httpd on


###虚拟内存

服务器1G的内存，编译不了MySQL，编译时出现以下错误：
virtual memory exhausted: Cannot allocate memory

**解决方法：**

发生该问题的原因是服务器的内存不够，从而导致编译失败。

而购买的Linux服务器，未给你分配虚拟内存，所以可以通过自行增加虚拟内存的方法予以解决：

wap分区的扩展很简单，但是需要root用户权限


dd if=/dev/zero of=/swapfile bs=1M count=2048(从/分区分出2048x1M大小的空间，挂在/swapfire上，成功会有输出)

mkswap /swapfile (格式化成swap格式)

swapon /swapfile (激活/swapfire，加入到swap分区中)

echo "/swapfile swap swap sw 0 0" &gt;&gt; /etc/fstab(开机自启动新添加的swap分区)


**删除swap分区**
swapoff /swapfile # 首先停止swap分区
rm -rf /swapfile # 删除swap分区文件


## FTP
yum install -y vsftpd 
vi /etc/vsftpd/vsftpd.conf
/etc/vsftpd.user_list

service name: vsftpd


## SSH

service sshd start


ps -ef|grep mysqld
kill -9 pid


unzip
yum install -y unzip zip；

yum install -y zip
