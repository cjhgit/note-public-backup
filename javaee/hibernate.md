[TOC]

&lt;id name="id" type="int" column="ID"&gt;
//该句指定使用hibernate自带的increment策略生成主键
&lt;generator class="increment"/&gt;
&lt;/id&gt;
 
session.save不用设置主键
 
 
 
常用的三种：uuid、native、assigned。uuid是Hibernate自动生成的一个字符串，一个被编码为32位16进制数字的字符串，save()前生成；native，自增，save()后生成；assigned，自己手动给主键赋值，save()前生成。
 
详细如下：
 
increment
用于为long, short或者int类型生成 唯一标识。只有在没有其他进程往同一张表中插入数据时才能使用。 在集群下不要使用。
 
identity
对DB2,MySQL, MS SQL Server, Sybase和HypersonicSQL的内置标识字段提供支持。 返回的标识符是long, short 或者int类型的。
 
sequence
在DB2,PostgreSQL, Oracle, SAP DB, McKoi中使用序列（sequence)， 而在Interbase中使用生成器(generator)。返回的标识符是long, short或者 int类型的。
 
hilo
使用一个高/低位算法高效的生成long, short 或者 int类型的标识符。给定一个表和字段（默认分别是 hibernate_unique_key 和next_hi）作为高位值的来源。 高/低位算法生成的标识符只在一个特定的数据库中是唯一的。
 
seqhilo
使用一个高/低位算法来高效的生成long, short 或者 int类型的标识符，给定一个数据库序列（sequence)的名字。
 
uuid
用一个128-bit的UUID算法生成字符串类型的标识符， 这在一个网络中是唯一的（使用了IP地址）。UUID被编码为一个32位16进制数字的字符串。
 
guid
在MS SQL Server 和 MySQL 中使用数据库生成的GUID字符串。
 
native
根据底层数据库的能力选择identity, sequence 或者hilo中的一个。
 
assigned
让应用程序在save()之前为对象分配一个标示符。这是 &lt;generator&gt;元素没有指定时的默认生成策略。
 
select
通过数据库触发器选择一些唯一主键的行并返回主键值来分配一个主键。
 
foreign
使用另外一个相关联的对象的标识符。通常和&lt;one-to-one&gt;联合起来使用。
 
 
 
注解：
 
TABLE：使用一个特定的数据库表格来保存主键。
SEQUENCE：根据底层数据库的序列来生成主键，条件是数据库支持序列。
IDENTITY：主键由数据库自动生成（主要是自动增长型）
AUTO：主键由程序控制。
 
@GeneratedValue(strategy = GenerationType.IDENTITY)
 
 
 
@Transactional标记的方法，如果不涉及数据库的增删改，应该设为只读事务。一是为了效率，二是避免不小心修改了数据库的数据，因为修改数据库的数据不一定要调用update之类的方法，一个处于持久态的_对象被修改时也会导致数据库的修改。_
 
 
 
hibernate建议使用基本类型的包装类型
 
 
 
query.setParameter(“customername”,name);但是对于一些类型就必须写明映射类型，比如java.util.Date类型，因为它会对应Hibernate的多种映射类型，比如Hibernate.DATA或者Hibernate.TIMESTAMP。