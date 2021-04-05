# redis启动
## sentinel启动
redis-server conf --sentinel
## 最简启动（动态参数启动）
redis-server [--port port]
ps -ef|grep redis
netstat -antpl|grep redis
redis-cli -h ip -p port ping
## 配置文件启动
redis-server configPath

+ redis-server
+ redis-cli -h host -p port -a password
+ redis-benchmark
+ redis-check-aof
+ redis-check-dump
+ redis-sentinel
+ config get * #获取当前redis全部配置
+ ping
+ dbsize #计算key的总数，不会遍历全部key，是读取redis内置计数器【时间复杂度O(1)】


# QPS测试
```
>redis-benchmark -h 127.0.0.1 -p 6379 -c 50 -n 100000 -d 2
```

# 集群模式客户端
```
redis-cli -c -p port
```
