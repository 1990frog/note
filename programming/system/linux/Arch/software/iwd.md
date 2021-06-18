[TOC]

# 操作页面
```
> iwctl
```

# 查询网卡驱动
```
> device list
wlan0
```

# 查询可链接wifi
```
> station device(wlan0) get-networks
```

# 连接wifi
```
> station device(wlan0) connect SSID
# 参数方式连接
> iwctl --passphrase passphrase station device connect SSID
```

# 断开网络
```
> station device disconnect
```

# 管理已知的网络
```
> known-networks list
```
# 忘记已知网络
```
> known-networks SSID forget
```