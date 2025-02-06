[TOC]

# 内核选择
+ Stable — 原版的 Linux 内核以及模块, 使用了一些补丁
+ Hardened — 更加注重安全的 Linux 内核，采用一系列 加固补丁 以减少内核和用户空间产生漏洞的风险
+ Longterm — 包含了长期支持的 Linux 内核和内核模块
+ Zen Kernel — 一些内核黑客合作的结果，提供了适合日常使用的优秀内核

# 切换内核
## 查看内核版本
```
> uname -r
6.4.12-arch1-1
```

## 安装新内核
```
> sudo pacman -S linux linux-headers
> sudo pacman -S linux-zen linux-zen-headers
```

## 卸载现有内存
```
> sudo pacman -Rs linux linux-headers
> sudo pacman -Rs linux-zen linux-zen-headers
```