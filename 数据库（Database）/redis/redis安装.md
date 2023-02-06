# redis安装

## linux
1. 下载
2. cd redis/
3. make
4. cd src
5. make install

## windows
### 下载
https://github.com/MSOpenTech/redis/releases

### 解压

### 运行
redis-server

### 注册服务
redis-server.exe --service-install redis.windows.conf


卸载服务：redis-server --service-uninstall

开启服务：redis-server --service-start

停止服务：redis-server --service-stop

重命名服务：redis-server --service-name name

redis-server --service-start

