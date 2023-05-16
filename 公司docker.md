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