# 环境搭建

## Windows

## Cent OS

## tmp

wget http://download.redis.io/releases/redis-3.2.0.tar.gz

tar xzf redis-2.8.3.tar.gz 
make && make install

redis-benchmark  redis-check-aof  redis-check-dump  redis-cli  redis-server

按以上步骤安装Redis时，其服务脚本位于：
/usr/local/src/redis/utils/redis_init_script 
必须将其复制到/etc/rc.d/init.d的目录下：
cp /root/redis-3.2.0/utils/redis_init_script /etc/rc.d/init.d/redis

如果这时添加注册服务：


chkconfig --add redis
将报以下错误：
service redis does not support chkconfig

解决：
vi /etc/rc.d/init.d/redis
1.第2行改成
#chkconfig: 2345 80 90 
2.EXEC、CLIEXEC参数，也是有所更改。 
EXEC=/usr/local/redis/bin/redis-server   
CLIEXEC=/usr/local/redis/bin/redis-cli 
3.redis开启的命令，以后台运行的方式执行。
$EXEC $CONF & 
ps:注意后面的那个“&”，即是将服务转到后面运行的意思，否则启动服务时，Redis服务将 
占据在前台，占用了主用户界面，造成其它的命令执行不了。 
4.将redis配置文件拷贝到/etc/redis/${REDISPORT}.conf 
mkdir /etc/redis    
cp  redis/redis.conf /etc/redis/6379.conf
这样，redis服务脚本指定的CONF就存在了。默认情况下，Redis未启用认证，可以通过开启6379.conf的requirepass 指定一个验证密码。 

以上操作完成后，即可注册yedis服务：
chkconfig --add redis
3.启动redis服务 
service redis start 


/*
启动Redis服务
redis-server redis.conf

  4、然后用客户端测试一下是否启动成功。
$ redis-cli redis> set foo bar OK redis> get foo "bar"

*/

.Redis的关闭

src/redis-cli shutdown

第三，将Redis的命令所在目录添加到系统参数PATH中 

修改profile文件：

vi /etc/profile
在最后行追加: 

export PATH="$PATH:/usr/local/redis/bin"
然后马上应用这个文件： 

. /etc/profile  
这样就可以直接调用redis-cli的命令了，如下所示： 

redis-cli   
redis 127.0.0.1:6379> auth superman   
OK   
redis 127.0.0.1:6379> ping   
PONG   
redis 127.0.0.1:6379>
至此，redis 就成功安装了。 












# redis（2.8）

## 安装
下载地址：https://github.com/dmajkic/redis/downloads

打开一个cmd窗口  使用cd命令切换目录到E:\TRS\redis 运行 redis-server.exe redis.conf 
如果想方便的话，可以把redis的路径加到系统的环境变量里，这样就省得再输路径了，
后面的那个redis.conf可以省略，如果省略，会启用默认的。

这时候别启一个cmd窗口，原来的不要关闭，不然就无法访问服务端了
切换到redis目录下运行 redis-cli.exe -h 127.0.0.1 -p 6379

windows 开机自动启动redis

REG ADD HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run /v TTplayerLaunch /t REG_EXPAND_SZ /d "D:\redis-2.0.0\redis-server.exe redis.conf"

将上面的内容放到文件redis.conf中，保存重命名这个文件为redis.bat,双击这个文件,redis就可以自动运行了，这样就不需要每次都打开一个windows窗口了。


后台运行：
首先你要安装服务：
redis-server --service-install redis.windows.conf --loglevel verbose
然后就可以启动了：
redis-server --service-start
卸载可以使用
redis-server --service-uninstall
