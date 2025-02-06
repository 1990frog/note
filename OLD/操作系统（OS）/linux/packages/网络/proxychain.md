[TOC]

# 安装
sudo pacman -S proxychains

# 配置
```
> vim /etc/proxychains.conf
+ socks5  127.0.0.1 7890
```

# 测试
curl www.youtube.com