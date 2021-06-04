[[TOC]]

# 离线安装
## 下载
[download](https://download.docker.com/linux/static/stable/x86_64/)

## 解压安装包
```
> tar zxf docker.tgz
```

## 将docker 相关命令拷贝到 /usr/bin
```
> cp docker/* /usr/bin/
```

## 启动守护进程
```
> dockerd &
```

## service
```
# sudo vi /usr/lib/systemd/system/docker.service

[Unit]
Description=Docker Application Container Engine
Documentation=https://docs.docker.com
After=network-online.target firewalld.service
Wants=network-online.target
 
[Service]
Type=notify
ExecStart=/usr/bin/dockerd
ExecReload=/bin/kill -s HUP $MAINPID
LimitNOFILE=infinity
LimitNPROC=infinity
TimeoutStartSec=0
Delegate=yes
KillMode=process
Restart=on-failure
StartLimitBurst=3
StartLimitInterval=60s
 
[Install]
WantedBy=multi-user.target
```
