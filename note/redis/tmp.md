
##### [建议] 尽可能使用过期时间

##### [建议] 合理的命名

使用合适的命名方法会简化你的数据库管理，当你通过你的应用程序或者服务做键的命名空间时（通常情况下是使用冒号来划分键名），你就可以在数据迁移、转换或者删除时轻松的识别。

推荐的命名方式是 [项目名：]表名：主键值：列名

如：[eim:]user:1000:password

##### [建议] 不存储业务实体
一般来讲业务实体随着业务的变更会有较频繁的变化，在传统的基于sql的数据库中，通过ORM有较完善和简便的解决方案。而在Redis中，业务实体是通过序列化成字节数组的方式保存，然后通过反序列化来获取该实体，如果实体发生了变化，将发生无法正确序列化的问题。

综上所述，我们建议只用Redis来持久化字符串或者Map形式的数据。当然如果有以下两种情况则可以特殊考虑：

* 实体简单并且没有太重要的业务意义，或者在很长时间内不会变化
* 实体已经在sql数据库中持久化，仅仅通过Redis进行缓存




Redis哨兵机制

redis实现发布/订阅
http://www.tianmaying.com/tutorial/springboot-redis-message



作为一个电商网站被各种spam攻击是少不免（垃圾评论、发布垃圾商品、广告、刷自家商品排名等）

使用场景：
热数据缓存（比如feed，数据库、缓存同时写、缓存主页）
评论数 或者是 点赞数 类似的功能
消息队列（广播、用于群发消息、通知类、延迟更新类）List数据结构实现分布式的消息队列。

1. 用户的token信息
2. 好友关系、用户的关注关系（以及被关注）

3，锁，用于并发的时候保持唯一性
3. 热点列表数据缓存（首页、热门话题等）

1.用key-hash保存用户关系。优点快速获取用户的关注以及粉丝数，也可以通过求交属性快速获取两个人的共同关注，共同粉丝；缺点：单线程单核计算，一次拿过多的key可能导致cpu到100%从而死机，共同关注一般ok，基本每个人关注用户数目差不多，共同粉丝不太适合微博这种媒体性质有大v的社交产品。
2. key-list，可以做队列，也可以作为用户的feeds流，在推模式下，来一个feed，list追加即可，也可以比较容易的截断设计feeds数目上限（媒体性质的社交不适合，要推送的太多）
3. key-sorted_set，可以认为是一个带有分数权重的优先级队列，在feeds流下可以用这个做自定义的排序，只要塞入feed时加入合适分数；还有做一个实时的排行榜也很容易，可以理解为一个大顶堆。缺点：很吃类存
4. key-string，有点像mc，但是这个string可以变，可以追加。
5. key-所有都可以根据业务和数据结构作为缓存

再比如论坛最新发表列表


利用 expire 做网站的 session

选择activemq高速队列做整流作用


4）WebSocket不同版本的几种握手方式
a）、无安全key、最老的WebSocket握手协议的实现（Flash）；
b）、带两个安全key请求头的后端握手实现；
c）、带一个安全key请求头的后端握手实现；
参见：http://blog.csdn.net/fenglibing/article/details/7100070


netty websocket
http://www.itstack.org/?post=15


2、任何涉及到使用redis读写的代码一定要使用try catch语句包裹，否则可能出现redis读写超时（如服务器与Redis服务器之间有网络延迟）或者其他异常导致redis链接对象无法放回连接池中。


opsForXXX和boundXXXOps的区别？

XXX为value的类型，前者获取一个operator，但是没有指定操作的对象（key），可以在一个连接（事务）内操作多个key以及对应的value；后者获取了一个指定操作对象（key）的operator，在一个连接（事务）内只能操作这个key对应的value。

关于计数的API（increment）有一个bug，需要各位使用中注意，通过increment计数以后，通过get方式获取计数值的时候可能会抛出EOF异常（和本地的jdk以及redis的编译版本有关），可以考虑使用boundValueOps(key).get(0,-1)获取计数值。


spring aop切面方式进行缓存
http://m.blog.csdn.net/article/details?id=50515320


=====================

系统并没有根据Cookie来做跟踪记录，只是根据IP来，所以统计结果上可能有点出入，会少统计些。

统计每天访问的UV，PV，来自百度的访问IP，推广来源IP数，还有就是一跳率信息
PV(访问量)：即Page View, 即页面浏览量或点击量，用户每次刷新即被计算一次。
　　UV(独立访客)：即Unique Visitor,访问您网站的一台电脑客户端为一个访客。00:00-24:00内相同的客户端只被计算一次。
　　IP(独立IP)：指独立IP数。00:00-24:00内相同IP地址之被计算一次。
=====================

推送服务，消息队列

TOP N话题

做IM的时候 用户消息 用户关系 各种数据 非持久化的都在redis里面


令牌桶算法(token bucket)

商品维度计数（喜欢数，评论数，鉴定数，浏览数,etc）

HSET product:1231233 like 5
HSET user:100000 follow 5

譬如将用戶的好友/粉丝/关注，可以存在一个sorted set中，score可以是timestamp，这样求两个人的共同好友的操作，可能就只需要用求交集命令即可。

redis> ZADD user:100000:follow 61307510400000 "100001" //score 为timestamp
(integer) 1
redis> ZADD user:100000:follow 61307510402300 "100002"
(integer) 1
redis> ZADD user:100000:follow 61307510405600 "100003"
(integer) 1
redis> ZADD user:200000:follow 61307510400000 "100001"
(integer) 1
redis> ZADD user:200000:follow 61307510402300 "100005"




NOTE: RPUSH pagewviews.user: EXPIRE pagewviews.user: 60 //注意要update timeout

4. 反spam系统（论坛发贴，etc）

譬如：1分钟评论不得超过2次、5分钟评论少于5次等（更多机制/规则需要结合drools ）。 采用sorted set将最近一天用户操作记录起来（为什么不全部记录？节省memory，全部操作会记录到log，后续利用hadoop进行更全面分析统计），通过ZRANGEBYSCORE user:200000:operation:comment 61307510405600 +inf 获得1分钟内的操作记录， redis> ZADD user:200000:operation:comment 61307510402300 "这是一条评论" //score 为timestamp (integer) 1 redis> ZRANGEBYSCORE user:200000:operation:comment 61307510405600 +inf//获得1分钟内的操作记录 1) "这是一条评论"


5. 用户Timeline/Feeds
user:100000:feed:topic  61307510400000

在逛 有个类似微博的栏目

6. 最新列表&排行榜（用户刚刚喜欢的商品，etc）





点击数喜欢数先写在redis里，然后每隔一段时间flush到db里去就好了。
等你的论坛已经大到计数会影响性能的时候，这一段时间的延迟已经根本不是问题了。

实测统计数据先存在redis然后再写入数据库，对于每分钟批量更新约15000请求来说，在一台i5的机器上CPU消耗不会超过5%。
根本不是瓶颈。



1.取最新N个数据的操作
比如典型的取你网站的最新文章，通过下面方式，我们可以将最新的5000条评论的ID放在Redis的List集合中，并将超出集合部分从数据库获取
使用LPUSH latest.comments<ID>命令，向list集合中插入数据
插入完成后再用LTRIM latest.comments 0 5000命令使其永远只保存最近5000个ID
然后我们在客户端获取某一页评论时可以用下面的逻辑（伪代码）
FUNCTION get_latest_comments(start,num_items):
    id_list = redis.lrange("latest.comments",start,start+num_items-1)
    IF id_list.length < num_items
        id_list = SQL_DB("SELECT ... ORDER BY time LIMIT ...")
    END
    RETURN id_list
END
如果你还有不同的筛选维度，比如某个分类的最新N条，那么你可以再建一个按此分类的List，只存ID的话，Redis是非常高效的。
2.排行榜应用，取TOP N操作
这个需求与上面需求的不同之处在于，前面操作以时间为权重，这个是以某个条件为权重，比如按顶的次数排序，这时候就需要我们的sorted set出马了，将你要排序的值设置成sorted set的score，将具体的数据设置成相应的value，每次只需要执行一条ZADD命令即可。
3.需要精准设定过期时间的应用
比如你可以把上面说到的sorted set的score值设置成过期时间的时间戳，那么就可以简单地通过过期时间排序，定时清除过期数据了，不仅是清除Redis中的过期数据，你完全可以把Redis里这个过期时间当成是对数据库中数据的索引，用Redis来找出哪些数据需要过期删除，然后再精准地从数据库中删除相应的记录。

7.Pub/Sub构建实时消息系统
Redis的Pub/Sub系统可以构建实时的消息系统，比如很多用Pub/Sub构建的实时聊天系统的例子。
8.构建队列系统
使用list可以构建队列系统，使用sorted set甚至可以构建有优先级的队列系统。


远程连接redis

h <主机ip>，默认是127.0.0.1

-p <端口>，默认是6379

-a <密码>，如果redis加锁，需要传递密码

--help，显示帮助信息

通过对rendis-cli用法介绍，在101上连接103应该很简单：

redis-cli -h 139.129.8.246 -p 6379 





chkconfig --list如果列表中没有mysqld这个，需要先用这个命令添加：

chkconfig add mysqld

然后用这个命令设置开机启动：

chkconfig mysqld on
chkconfig apache on 设置开机启动。
chkconfig –add httpd

apachectl -k graceful  



储存用户信息，比如会话、配置文件、参数、购物车等等。这些信息一般都和ID（键）挂钩，这种情景下键值数据库是个很好的选择。


总结一下：1 一般的高并发的应用程序，都在web层采用了以上几种缓存，一般静态资源（图片，js，css）都会采用nginx反向代理+客户端缓存来实现。

              2  对于门户网站，尤其是首页的新闻，一般都会缓存起来，可以通过反向代理也可以通过应用程序缓存实现方式

              3 对于下载或者视频网站，由于数据传输比较大，直接采用浏览器本地缓存实现。




Web层采用了动态页面静态化技术，超过一定 
时间的文章生成静态HTML文件


换一种实现思路，用redis做缓存，消息到达服务器的时候，并不是立刻插入数据库，而是存在redis里。当redis聊天记录到达60条的时候，再执行1次数据库插入操作。

Saas

Redis这个Nosql的存储系统一般会被部署到linux系统中，我们可以把它当成是一个数据服务器，对于并发理大时，我们会使用多台服务器充当Redis服务器，这时，各个Redis之间也是分布式的，而Redis与WWW之间也是一种分布式，对于各个redis之间的分布式不需要我们去干预，它是由我们的redis客户端去负责链接的，你当时链到哪台服务器，完全由客户端去控制，redis这种模式我们通常称为“主从模式”，即一个主服务器，主要负责写入数据，多台从服务器，负责数据的读取，而它们之前的数据同步，也是redis自已为我们实现的，我们不需要去干预它，这种模式通常会称为“多级服务器集群架构”，它大大改善了程序的性能！


如将键名very.important.person:20改成VIP:20。


一般使用冒号做分割符，这是不成文的规矩。
login:2:login_times
login:2:last_login_time
login:2:name

book:1:name
book:1:author




先把key找到,再判断这个key是否已经过期(自动联想我们看一个面包是否已经过期...).
如果已经过期了, redis就不给我们返回对应的value值了. 这是redis 处理key过期的active方式,


1.随机抽取100个设定了有效期的key,检查其有效期,如果已经过期,则将其删除.

2.如果抽取到的100个key中超过25个已经过期,那么返回步骤1,

这就是redis中清除已经过期的key的 passive 方法.


Session钝化机制的本质就在于把服务器中不经常使用的Session对象暂时序列化到系统文件系统或是数据库系统中，当被使用时反序列化到内存中，整个过程由服务器自动完成。

实现：

         要完成session持久化，存放在session里的对象必须要实现java.io.Serializable 接口。



所以我觉得，最最靠谱的方法是在robots.txt里放上钓鱼连接。
正常的搜索引擎不会去访问，不遵守robots规定的也被禁止了。







