主键
应尽量避免在库表中引入与业务逻辑相关的主键关系。 复合主键的引入，很大程度上意味着业务逻辑已经侵入到数据存储逻辑之中。   主键可以保证记录的唯一和主键域非空，数据库管理系统对于主键自动生成唯一索引，所以主键也是一个特殊的索引。 2. 一个表中可以有多个唯一性索引，但只能有一个主键。 3. 主键列不允许空值，而唯一性索引列允许空值。 4. 索引可以提高查询的速度。 在数据库关系图中为表定义主键将自动创建主键索引，主键索引是唯一索引的特定类型。 唯一索引、主键索引和聚集索引 在聚集索引中，表中行的物理顺序与键值的逻辑（索引）顺序相同。一个表只能包含一个聚集索引。 唯一索引允许NULL值并且一般不能用在指示性约束中 唯一约束不允许NULL值并能在外键规范中使用   mysql中text 最大长度为65,535(2的16次方–1)字符的TEXT列。 如果你觉得text长度不够，可以选择 MEDIUMTEXT最大长度为16,777,215。 LONGTEXT最大长度为4,294,967,295 bigint 从 -2^63 (-9223372036854775808) 到 2^63-1 (9223372036854775807) 的整型数据（所有数字）。存储大小为 8 个字节。 int 从 -2^31 (-2,147,483,648) 到 2^31 – 1 (2,147,483,647) 的整型数据（所有数字）。存储大小为 4 个字节。int 的 SQL-92 同义字为 integer。 smallint 从 -2^15 (-32,768) 到 2^15 – 1 (32,767) 的整型数据。存储大小为 2 个字节。 tinyint 从 0 到 255 的整型数据。存储大小为 1 字节。 当只要一行数据时使用 LIMIT 1 为搜索字段建索引   我们应该为数据库里的每张表都设置一个INT类型的自增ID做为其主键（推荐使用UNSIGNED） 使用 VARCHAR 类型来当主键会使用得性能下降。   集群，分区……   数据库、表切分 逻辑数据库设计 – 需要ID(谈主键Id)  
我想不仅仅是Oracle,其他数据库也一样的,Unique约束和Primary key约束用来保证同一表中指定的列上没有重复值，这两个约束都产生唯一索引确保数据一致性，默认情况下，Unique约束产生唯一的非聚集索引，Primary key约束产生唯一的聚集索引。Primary key约束比Unique约束严格：Primary key列不允许有空值，
SQLServer自动在主键上创建聚集索引，在UNIQUE约束列上创建非聚集索引



* UTC 时间
* 各国时间不同
* wordpress 时间
* 电脑上显示的时间是国际时间？
* 我们现在用的时间是北京时间吗？



You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'cource /root/luminiaq_net.sql' at line 1




MySql5.6操作时报错：You must SET PASSWORD before executing this statement解决
mysql>  SET PASSWORD = PASSWORD('123456');
Query OK, 0 rows affected (0.03 sec)


2017-02-09 23:38:14 10673 [ERROR] InnoDB: Cannot allocate memory for the buffer pool
2017-02-09 23:38:14 10673 [ERROR] Plugin 'InnoDB' init function returned error.
2017-02-09 23:38:14 10673 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
2017-02-09 23:38:14 10673 [ERROR] Unknown/unsupported storage engine: InnoDB
2017-02-09 23:38:14 10673 [ERROR] Aborting
