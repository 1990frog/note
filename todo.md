# linux
+ lazygit

# java
+ stream
+ newdate

# maven


---

day 

# 20220214
+ spark little



mysql分库分表与分布式差别


HDFS全称是Hadoop Distributed File System，是Hadoop的分布式文件系统。
它由很多机器组成，每台机器上运行一个DataNode进程，负责管理一部分数据。然后有一台机器上运行了NameNode进程，NameNode大致可以认为是负责管理整个HDFS集群的这么一个进程，他里面存储了HDFS集群的所有元数据。然后有很多台机器，每台机器存储一部分数据！好，HDFS现在可以很好的存储和管理大量的数据了。这时候你肯定会有疑问：MySQL服务器也不是这样的吗？你要是这样想，那就大错特错了。这个事情不是你想的那么简单的，HDFS天然就是分布式的技术，所以你上传大量数据，存储数据，管理数据，天然就可以用HDFS来做。如果你硬要基于MySQL分库分表这个事儿，会痛苦很多倍，因为MySQL并不是设计为分布式系统架构的，他在分布式数据存储这块缺乏很多数据保障的机制。


分布式数据库


mysql是用来支持OLTP workload的，就是大量的单行查询。

mysql本身不是为分布式设计的，但是后来大家发现一个机器存不下那么多机器所以就开始搞分布式了。现在多数的做法还是sharding。

hadoop是用来处理OLAP workload的，就是大量的scan，大量的aggregation。hadoop本身就是为分布式设计的。

mysql+hadoop当然是可以的，而且应该算是很经典的用例。mysql数据库在前端跑，然后每隔一段时间比如每天把mysql的数据导入到hadoop中做数据分析。
