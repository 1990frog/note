# mysql
docker run -itd -p13306:3306 -e MYSQL_ROOT_PASSWORD=P@ssw0rd --name dqmysql dqmysql:suzhou

# redis
docker run -itd --name dqredis -p16379:6379 redis --requirepass P@ssw0rd

# mongo
docker run -d -p27017:27017 -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=P@ssw0rd --name=dqmongo  mongo

# dqall
docker run -itd -p18848:8848 -p37077:37077 -p17077:7077 -p15000:5000 --name dqall dqall:suzhou




# 构建
docker build -f Dockerfile.debian -t dqmysql:suzhou .
docker build -f Dockerfile.centos8.py310.all -t dqall:suzhou .


docker save mongo -o mongo.tar
docker save dqall:suzhou -o dqservice.tar
save dqmysql:suzhou -o dqmysql.tar
save redis -o redis.tar


docker load -i mongo.tar
docker load -i dqservice.tar
docker load -i dqmysql.tar
docker load -i redis.tar

# 新版工作安排
+ 首次登录操作指南
+ 未配置机构设置规则为模板类型
+ 普通规则转成模板规则
+ 首页性能优化
+ xxljob接入
+ 问题稽查逻辑
+ 执行任务直接加任务id
+ 机构停用核查
+ 模型停用核查
+ 质量评估报告三合一
+ 提示框优化
+ 菜单刷新
+ 元数据配置类型
+ 时间类型为字符串转型
+ 主数据改造
+ jdbc超时
+ jdbc监控
+ 错误记录
+ 日志记录
+ 规则配置，规则类型下拉显示完整
+ 模板规则备注优化
+ 全页面空补
+ 字段类型多选
+ 任务创建成功返回任务列表
+ 模板规则创建任务，机构使用传递参数的规则（OK）