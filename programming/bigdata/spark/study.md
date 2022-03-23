sql on hadoop
使用sql语句对大数据进行分析，数据是在hadoop

apache hive
sql转换成一系列可以在hadoop上允许的mp/tez/spark作业
sql到底底层是运行在哪种分布式引擎之上的，是可以通过一个参数来设置
功能：
1.sql：命令行、代码
2.多语言Apache Thrift驱动
3.自定义的UDF函数：按照标准接口实现，打包，加载到Hive中

cloudera impala
使用了自己的执行守护进程集合，一般情况下这些进程是需要与hadoop dn安装在一个节点上
功能：
1、92sql支持
2、hive支持
3、命令行、代码
4、与hive能够共享元数据
5、基于内存

spark sql
spark中的一个子模块，
hive：sql=》mapreduce
spark：sql直接运行在spark引擎之上（0.8版本shark现在没有了，sql=》spark，优点：快，与hive能够兼容，缺点：执行计划优化完全依赖于hive，mr是进程级别，spark是线程级别。使用：需要独立维护一个打了补丁的hive源码分支）

====》
1） spark sql
sql，是spark里面额
2） hive on spark
hive里面的，通过切换hive的执行引擎即可，底层添加了spark执行引擎的支持


presto
交互式查询引擎，sql
功能：
1、共享元数据信息
2、92语言
3、提供了一系列的连接器，Hive Cassandra ... 

Drill
HDFS、hive、spark sql
支持多种后端存储，然后直接进行各种后端数据的处理

Phoenix
hbase的数据，是要基于api进行查询
phoenix使用sql来查询hbase中的数据
主要点：如果想查询的快的话，还是要取决于ROWKEY的设计


---

spark sql 是什么
spark sql is apache spark's module for working with structured data.

误区一：spark sql就是一个sql处理框架
1）集成性：在spark编程中无缝对接多种复杂的sql
2）统一额数据访问方式：以类事都得方式访问多种不同的数据源，而且可以进行相关操作
spark.read.format("json").load(path)
spark.read.format("text").load(path)
spark.read.format("parquet").load(path)
spark.read.format("json").option("jdbc信息").load(path)
3）兼容hive
allowing you to access existing hive warehouses
如果你想把hive的作业迁移到spark sql，这样的话，迁移成本就会低很多
前提：共享meta store
4）标准的数据连接：提供标准的JDBC/ODBC连接方式

spark sql应用并不局限于sql，还支持hive、json、parquet文件的直接读取以操作
sql仅仅是spark sql中的一个功能而已