<!-- TOC -->

- [逻辑上](#%E9%80%BB%E8%BE%91%E4%B8%8A)
- [物理上](#%E7%89%A9%E7%90%86%E4%B8%8A)
- [索引结构](#%E7%B4%A2%E5%BC%95%E7%BB%93%E6%9E%84)
    - [B-tree](#b-tree)
    - [Bitmap](#bitmap)

<!-- /TOC -->

# 逻辑上
+ Single column 单行索引
+ Concatenated 多行索引
+ Unique 唯一索引
+ NonUnique 非唯一索引
+ Function-based函数索引
+ Domain 域索引

# 物理上
+ Partitioned 分区索引
+ NonPartitioned 非分区索引
+ B-tree：
Normal 正常型B树
Rever Key 反转型B树
Bitmap 位图索引

# 索引结构
## B-tree
+ 适合与大量的增、删、改（OLTP）
+ 不能用包含OR操作符的查询
+ 适合高基数的列（唯一值多）
+ 典型的树状结构
+ 每个结点都是数据块
+ 大多都是物理上一层、两层或三层不定，逻辑上三层
+ 叶子块数据是排序的，从左向右递增
+ 在分支块和根块中放的是索引的范围
## Bitmap
+ 适合与决策支持系统
+ 做UPDATE代价非常高
+ 非常适合OR操作符的查询
+ 基数比较少的时候才能建位图索引


1. b-tree索引
Oracle数据库中最常见的索引类型是b-tree索引，也就是B-树索引，以其同名的计算科学结构命名。CREATE 
INDEX语句时，默认就是在创建b-tree索引。没有特别规定可用于任何情况。
2. 位图索引(bitmap index)
位图索引特定于该列只有几个枚举值的情况，比如性别字段，标示字段比如只有0和1的情况。
3. 基于函数的索引
比如经常对某个字段做查询的时候是带函数操作的，那么此时建一个函数索引就有价值了。
4. 分区索引和全局索引
这2个是用于分区表的时候。前者是分区内索引，后者是全表索引
5. 反向索引（REVERSE）
这个索引不常见，但是特定情况特别有效，比如一个varchar(5)位字段(员工编号)含值
（10001,10002,10033,10005,10016..）
这种情况默认索引分布过于密集，不能利用好服务器的并行
但是反向之后10001,20001,33001,50001,61001就有了一个很好的分布，能高效的利用好并行运算。
6. HASH索引
HASH索引可能是访问数据库中数据的最快方法，但它也有自身的缺点。集群键上不同值的数目必须在创建HASH集群之前就要知道。需要在创建HASH集群的时候指定这个值。使用HASH索引必须要使用HASH集群。
