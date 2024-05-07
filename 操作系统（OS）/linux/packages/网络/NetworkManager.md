[TOC]

# 安装
`sudo pacman -S networkmanager`
KDE模块
`sudo pacman -S plasma-nm`

# 创建服务
```
> systemctl start NetworkManager
> systemctl enable NetworkManager
```

# 命令
显示附近的网络
nmcli device wifi list

连接到指定网络
nmcli device wifi connect SSID password 密码