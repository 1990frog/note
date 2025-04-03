[TOC]

# 避免使用 select *
1. 数据传输量大，返回所有的字段会导致不必要的网络传输，尤其涉及到大字段如 BLOB、TEXT 等字段，数据量可能成倍增长，增加带宽压力和响应时间。




使用 union all 替代 union

小表驱动大表
in 适用于左边大表，右边小表
exists 适用于左边小表，右边大表

批量操作
把握度

多用limit


in值太多

分页
高效分页
limit 分页性能问题

limit 10000,20
替换为
id > 10000 limit 20
该方案要求id连续



连接查询替代子查询


join 表不要太多

left join 默认用左边的表驱动右边的a表

控制索引数量
阿里巴巴单表最多索引5个
b+tree索引

高并发表如何建立索引？能建立联合索引就不要建立但字段索引

选择合理的字段类型

char varchar

能用数值类型就不用字符串，用bit存boolean值，用tinyint存枚举值，长度固定的用char，长度不定的用varchar。金额字段用decimal，日期字段用date，时间戳字段用datetime。

group by + having 不如在分组之前过滤数据

explain 分析sql

