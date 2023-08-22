<!-- TOC -->

- [操作页面](#%E6%93%8D%E4%BD%9C%E9%A1%B5%E9%9D%A2)
- [查询网卡驱动](#%E6%9F%A5%E8%AF%A2%E7%BD%91%E5%8D%A1%E9%A9%B1%E5%8A%A8)
- [查看驱动情况](#%E6%9F%A5%E7%9C%8B%E9%A9%B1%E5%8A%A8%E6%83%85%E5%86%B5)
- [查询可链接wifi](#%E6%9F%A5%E8%AF%A2%E5%8F%AF%E9%93%BE%E6%8E%A5wifi)
- [连接wifi](#%E8%BF%9E%E6%8E%A5wifi)
- [断开网络](#%E6%96%AD%E5%BC%80%E7%BD%91%E7%BB%9C)
- [管理已知的网络](#%E7%AE%A1%E7%90%86%E5%B7%B2%E7%9F%A5%E7%9A%84%E7%BD%91%E7%BB%9C)
- [忘记已知网络](#%E5%BF%98%E8%AE%B0%E5%B7%B2%E7%9F%A5%E7%BD%91%E7%BB%9C)

<!-- /TOC -->

# 操作页面
```
> iwctl
```

# 查询网卡驱动
```
> device list
wlan0
```

# 查看驱动情况
```
> station device(wlan0) show
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
> station device(wlan0) disconnect
```

# 管理已知的网络
```
> known-networks list
```

# 忘记已知网络
```
> known-networks SSID forget
```