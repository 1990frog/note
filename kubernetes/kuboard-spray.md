
[github](https://github.com/eip-work/kuboard-spray)
[在线文档](https://kuboard-spray.cn/)
[资源包](https://kuboard-spray.cn/support/)

```
docker run -d \
  --privileged \
  --restart=unless-stopped \
  --name=kuboard-spray \
  -p 80:80/tcp \
  -e TZ=Asia/Shanghai \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v ~/kuboard-spray-data:/data \
  eipwork/kuboard-spray:latest-amd64
  # 如果您是 arm64 环境，请将标签里的 amd64 修改为 arm64，例如 eipwork/kuboard-spray:latest-arm64
  # 如果抓不到这个镜像，可以尝试一下这个备用地址：
  # swr.cn-east-2.myhuaweicloud.com/kuboard/kuboard-spray:latest-amd64
```

用户名 admin
默认密码 Kuboard123