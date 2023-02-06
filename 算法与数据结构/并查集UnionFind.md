[TOC]

# 连接问题
+ 网络中节点间的连接状态（是否存在相同的路径）
+ 网络是个抽象的概念：用户之间形成的网络（关系扩散）
+ 数学中的集合类实现（并集）

# 并查集 UnionFind
对于一组数据，主要支持两个动作：
+ union(p,q)
+ isConnected(p,q)

```java
public interface UF {
    int getSize();
    int find(int p);
    boolean isConnected(int p,int q); //O(1)
    void unionElements(int p,int q); //O(n)
}
```

# 并查集的级别数据表示
```
0,1,2,3,4,5,6,7,8,9(id)
-------------------
0,0,0,0,0,1,1,1,1,1(集合)
```
# Quick Find
```java

```

# 升级Quick Union













rank pk size


# 路径压缩 Path Compression




rank不是深度也不是个数，仅是个排名

并查集的时间复杂度分析
O(h)严格意义上：O(log*n) iterated logarithm


log*n比logn还快，近乎是O(1)级别的

# 第一版并查集
集合中的元素都指向根节点
# 第二版并查集
子集的根节点指向新的根节点
# 第三版并查集
比较子集的size，缩短并查集的长度
# 第四版
基于rank的优化
第三版本如果size大的子集是树结构的且只有2层，那可能比size少的链表结构的还要简单
核心：降低高度，提高遍历速度