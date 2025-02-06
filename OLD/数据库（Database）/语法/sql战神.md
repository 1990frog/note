[TOC]

内嵌试图
标量子查询
窗口函数

```sql
select sal as salary,comm as commission
from emp
where salary < 5000
```
where 子句会比 select 子句先执行，别名无法解析

```sql
select * from 
(select sal as salary,comm as commission
from emp) x
where x.salary < 5000
```
from 子句优先于 where 子句执行

优先级：from > where > select


# 串联多列的值
```sql
# mysql
select concat(code,name) from table;
# oracle、db2、postgresql
select code || name from table;
# sqlserver
select code+name from table;
```

# 限定条数
```sql
# mysql&postgresql
select * from emp limit 5;

# oracle
select * from emp where rownum <= 5；

# sqlserver
select top 5 * from emp;
```

# 随机返回若干行
通过函数随机生成查询结果
```sql
#db2
select * from emp order by rand() fetch first 5 rows only;

# mysql
select * from emp order by rand() limit 5;

# postgresql
select * from emp order by random() limit 5;

# oracle
# 其他数据底层逻辑
select * from (select * from emp order by dbms_random.value()) where rownum < 5

# sqlserver
select top 5 * from emp order by newid();
```

# 返回第一个非空的值
coalesce