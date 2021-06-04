[TOC]

# 安装
```
pacman -S refind
```
# 运行
```
sudo /usr/bin/refind-install
```
# 配置文件
/boot/EFI/refind/refind.conf
```
# 等待时间
timeout 20
# 分辨率
resolution 3840 2160
dont_scan_volumes "Recovery HD"
# 不要扫描全部的内核
scan_all_linux_kernels false
# 引入主题
include themes/rEFInd-Theme/theme.conf
```