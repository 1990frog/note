[TOC]

![1289934-20190621163930814-1395015700](https://raw.githubusercontent.com/1990frog/imagebed/default/1602320094_20200414182139016_686851996.png)

+ string（变量）
+ hash（map）
+ list（链表）
+ set（映射）
+ zset

# string
单一key-value存储
![](https://raw.githubusercontent.com/1990frog/imagebed/default/1602320091_20191226160919508_1428409832.png)
## 业务场景
1. 缓存： 经典使用场景，把常用信息，字符串，图片或者视频等信息放到redis中，redis作为缓存层，mysql做持久化层，降低mysql的读写压力
2. 计数器：redis是单线程模型，一个命令执行完才会执行下一个，同时数据可以一步落地到其他的数据源
3. session：常见方案spring session + redis实现session共享
## 简介
string是redis最基本的类型，你可以理解成与Memcached一模一样的类型，一个key对应一个value。value其实不仅是String，也可以是数字。string类型是二进制安全的。意思是redis的string可以包含任何数据。比如jpg图片或者序列化的对象。string类型是Redis最基本的数据类型，string 类型的值最大能存储512MB。
## 应用场景
1. String是最常用的一种数据类型，普通的key/ value 存储都可以归为此类，即可以完全实现目前 Memcached 的功能，并且效率更高。还可以享受Redis的定时持久化，操作日志及 Replication等功能。
2. 常规key-value缓存应用。常规计数: 微博数, 粉丝数。 实现方式：String在redis内部存储默认就是一个字符串，被redisObject所引用，当遇到incr,decr等操作时会转成数值型进行计算，此时redisObject的encoding字段为int。
## 难点
位运算

# hash（映射）
命令都是h开头的
适用于存储对象，建立一个对象名称，对象中可以设立多个键值对作为属性。查询的时候通过一个对象名称获取其所有属性
![](https://raw.githubusercontent.com/1990frog/imagebed/default/1602320091_20191226160939740_1059692059.png)
哈希键值结构：key->[field,value]
hash分为两种(encoding)：hashtable、ziplist，如果量达到一定就会使用ziplist压缩节省内存
<font color="red">hash缺点：不能对key设置过期时间</font>
```
使用：所有hash的命令都是h开头的hget、hset、hdel等
redis> hset hashmap key1 name
redis> hset hashmap key2 name
```
## 实战场景
缓存，但是还是使用String存json比较好

# list（链表）
命令都是l开头的
List 说白了就是链表（redis 使用双端链表实现的 List），是有序的，value可以重复，可以通过下标取出对应的value值，左右两边都能进行插入和删除数据。
![](https://raw.githubusercontent.com/1990frog/imagebed/default/1602320092_20191226161001347_1266075473.png)
使用列表的技巧：
+ lpush+lpop=Stack(栈)
+ lpush+rpop=Queue（队列）
+ lpush+ltrim=Capped Collection（有限集合）
+ lpush+brpop=Message Queue（消息队列）

# set（集合）
命令都s开头的
集合类型也是用来保存多个字符串的元素，但和列表不同的是集合中：
1. 不允许有重复的元素
2. 集合中的元素是无序的，不能通过索引下标获取元素
3. 支持集合间的操作，可以取多个集合取交集、并集、差集

![](https://raw.githubusercontent.com/1990frog/imagebed/default/1602320092_20191226161101783_1056431316.png)

## 实战场景
1. 标签（tag）,给用户添加标签，或者用户给消息添加标签，这样有同一标签或者类似标签的可以给推荐关注的事或者关注的人。
2. 点赞，或点踩，收藏等，可以放到set中实现

给用户添加标签
```
sadd user:1:tags tag1 tag2 tag3
```
给用户添加标签
```
sadd tag1:users user1 user2
```

# zset（有序集合）
有序集合和集合有着必然的联系，保留了集合不能有重复成员的特性，区别是，有序集合中的元素是可以排序的，它给每个元素设置一个分数，作为排序的依据。
（有序集合中的元素不可以重复，但是score 分数 可以重复，就和一个班里的同学学号不能重复，但考试成绩可以相同）。

![](https://raw.githubusercontent.com/1990frog/imagebed/default/1602320093_20191226161123740_296686436.png)

实战场景：
1.排行榜：有序集合经典使用场景。例如小说视频等网站需要对用户上传的小说视频做排行榜，榜单可以按照用户关注数，更新时间，字数等打分，做排行。

