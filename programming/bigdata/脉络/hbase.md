[TOC]

# 概览
HBase是一个开源的非关系型分布式数据库（NoSQL），它参考了谷歌的BigTable建模，实现的编程语言为 Java

HBase在列上实现了BigTable论文提到的压缩算法、内存操作和布隆过滤器。HBase的表能够作为MapReduce任务的输入和输出

在 Eric Brewer的CAP理论中，HBase属于CP类型的系统

HBase是依赖Hadoop的。为什么HBase能存储海量的数据？因为HBase是在HDFS的基础之上构建的，HDFS是分布式文件系统。



# hbase存在的意义
MySQL？MySQL数据库我们是算用得最多了的吧？但众所周知，MySQL是单机的。MySQL能存储多少数据，取决于那台服务器的硬盘大小。以现在互联网的数据量，很多时候MySQL是没法存储那么多数据的。
比如我这边有个系统，一天就能产生1TB的数据，这数据是不可能存MySQL的。（如此大的量数据，我们现在的做法是先写到Kafka，然后落到Hive中）
Kafka？Kafka我们主要用来处理消息的（解耦异步削峰）。数据到Kafka，Kafka会将数据持久化到硬盘中，并且Kafka是分布式的（很方便的扩展），理论上Kafka可以存储很大的数据。但是Kafka的数据我们不会「单独」取出来。持久化了的数据，最常见的用法就是重新设置offset，做「回溯」操作
Redis？Redis是缓存数据库，所有的读写都在内存中，速度贼快。AOF/RDB存储的数据都会加载到内存中，Redis不适合存大量的数据（因为内存太贵了！）。
Elasticsearch？Elasticsearch是一个分布式的搜索引擎，主要用于检索。理论上Elasticsearch也是可以存储海量的数据（毕竟分布式），我们也可以将数据用『索引』来取出来，似乎已经是非常完美的中间件了。
但是如果我们的数据没有经常「检索」的需求，其实不必放到Elasticsearch，数据写入Elasticsearch需要分词，无疑会浪费资源。
HDFS？显然HDFS是可以存储海量的数据的，它就是为海量数据而生的。它也有明显的缺点：不支持随机修改，查询效率低，对小文件支持不友好。


（hdfs小文件问题）

HDFS和HBase有啥区别阿？

HDFS是文件系统，而HBase是数据库，其实也没啥可比性。「你可以把HBase当做是MySQL，把HDFS当做是硬盘。HBase只是一个NoSQL数据库，把数据存在HDFS上」。
扯了这么多，那我们为啥要用HBase呢？HBase在HDFS之上提供了高并发的随机写和支持实时查询，这是HDFS不具备的。

但HBase还有一个特点就是：存储数据的”结构“可以地非常灵活

# 列式存储
行式存储：
![](https://gitee.com/caijingquan/imagebed/raw/master/https://gitee.com/caijingquan/imagebed/v2-58697c09af0a80f04af4b2231e6a0813_r.jpg)
行式存储转换列式存储：
![](https://gitee.com/caijingquan/imagebed/raw/master/https://gitee.com/caijingquan/imagebed/v2-8b4c896c9decec36b89e6b2fee968c6a_r.jpg)

可以很简单的发现，无非就是把每列抽出来，然后关联上Id
Key-Value
很明显以前我们一行记录多个属性(列)，有部分的列是空缺的，但是我们还是需要空间去存储。现在把这些列全部拆开，有什么我们就存什么，这样空间就能被我们充分利用。

在HBase里边，定位一行数据会有一个唯一的值，这个叫做行键(RowKey)。而在HBase的列不是我们在关系型数据库所想象中的列。

HBase的列（Column）都得归属到列族（Column Family）中。在HBase中用列修饰符（Column Qualifier）来标识每个列。

在HBase里边，先有列族，后有列。

什么是列族？可以简单理解为：列的属性类别

什么是列修饰符？先有列族后有列，在列族下用列修饰符来标识一列。

![](https://gitee.com/caijingquan/imagebed/raw/master/https://gitee.com/caijingquan/imagebed/2021-11-14_15-39.png)

![](https://gitee.com/caijingquan/imagebed/raw/master/https://gitee.com/caijingquan/imagebed/2021-11-14_15-39_1.png)

![](https://gitee.com/caijingquan/imagebed/raw/master/https://gitee.com/caijingquan/imagebed/2021-11-14_15-47.png)

HBase表的每一行中，列的组成都是灵活的，行与行之间的列不需要相同

RowKey | Columns
-------|--------
Row1 | {id,name,phone}
Row2 | {id,name,address,title,email}

![](https://gitee.com/caijingquan/imagebed/raw/master/https://gitee.com/caijingquan/imagebed/v2-de19abe0e27b1660e3474bd11aaf8d61_r.jpg)

换句话说：一个列族下可以任意添加列，不受任何限制

数据写到HBase的时候都会被记录一个时间戳，这个时间戳被我们当做一个版本。比如说，我们修改或者删除某一条的时候，本质上是往里边新增一条数据，记录的版本加一了而已。

比如现在我们有一条记录：
![](https://gitee.com/caijingquan/imagebed/raw/master/https://gitee.com/caijingquan/imagebed/2021-11-14_15-52.png)

![](https://gitee.com/caijingquan/imagebed/raw/master/https://gitee.com/caijingquan/imagebed/2021-11-14_15-52_1.png)

# HBase的架构图

![](https://gitee.com/caijingquan/imagebed/raw/master/https://gitee.com/caijingquan/imagebed/v2-f9029a2beaf2b07d9ae949013ddca351_r.jpg)

1、Client客户端，它提供了访问HBase的接口，并且维护了对应的cache来加速HBase的访问。

2、Zookeeper存储HBase的元数据（meta表），无论是读还是写数据，都是去Zookeeper里边拿到meta元数据告诉给客户端去哪台机器读写数据

3、HRegionServer它是处理客户端的读写请求，负责与HDFS底层交互，是真正干活的节点。

总结大致的流程就是：client请求到Zookeeper，然后Zookeeper返回HRegionServer地址给client，client得到Zookeeper返回的地址去请求HRegionServer，HRegionServer读写数据后返回给client。










# 部署
conf文件夹
修改hbase-env.sh
添加java_home
```
export JAVA_HOME=...

# 默认使用hbase自带的zk，设置false启用搭建的zk
export HBASE_MANAGES_ZK=false
```

修改hbase-site.xml
```
<property>
    <name>hbase.rootdir</name>
    <value>hdfs://hadoop000:8020/hbase</value>
</property>

<property>
    <name>hbase.cluster.distributed</name>
    <value>true</value>
</property>

<property>
    <name>hbase.zookeeper.quorum</name>
    <value>...</value>
</property>
```

hbase 为啥要用zookpeeper