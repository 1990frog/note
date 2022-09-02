<!-- TOC -->

- [wiki](#wiki)
- [前期准备](#前期准备)
- [磁盘](#磁盘)
  - [分区](#分区)
  - [挂载](#挂载)
- [安装linux](#安装linux)
  - [安装软件仓库源](#安装软件仓库源)
  - [安装](#安装)
- [挂载](#挂载-1)
- [启动器](#启动器)
- [Chroot](#chroot)
- [设置时区](#设置时区)
- [本地化](#本地化)
- [主机名](#主机名)
- [用户](#用户)
- [驱动](#驱动)
  - [显示](#显示)

<!-- /TOC -->

# wiki
[General recommendations](https://wiki.archlinux.org/title/General_recommendations_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
[引导](https://wiki.archlinux.org/title/Arch_boot_process_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
[多媒体](https://wiki.archlinux.org/title/Category:Multimedia_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
[核心工具](https://wiki.archlinux.org/title/Core_utilities_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

# 前期准备
+ [下载](https://archlinux.org/download/)
+ rufus dd模式烧盘

# 磁盘
## 分区
[xdisk](../packages/xdisk.md)  
分两个区：
+ root
+ home

## 挂载
```
> mount /dev/nvme0n1p2 /mnt
> mkdir /mnt/boot
> mount /dev/nvme0n1p1 /mnt/boot
```

# 安装linux
## 安装软件仓库源
[reflector](../packages/reflector.md)
[pacman](../packages/pacman.md)

## 安装
```
> pacstrap /mnt linux linux-firmware base base-devel neovim dhcpcd iwd amd-ucode
```
+ linux 内核
+ linux-firmware 硬件驱动
+ base 基本的用户工具
+ base-devel 基础的开发工具
+ neovim 编辑器
+ dhcpcd 有线网卡
+ iwd 无线网卡
+ amd-ucode 微码

切记安装网络
[dhcpcd](../packages/dhcpcd.md)
[iwd](../packages/iwd.md)

# 挂载
uuid模式：`-U`，默认目录模式
```
> genfstab -U /mnt >> /mnt/etc/fstab
```

# 启动器
+ [refind 最佳](../packages/refind.md)
+ [bootctl](../packages/bootctl.md)
+ [grub](../packages/grub.md)


# Chroot 
进入系统
> arch-chroot /mnt

# 设置时区
```
> ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
> hwclock --systohc
```
坑：双系统UTC与local

# 本地化
Locale数据，用于控制操作系统的本地化，以支持不同的语音、时间格式等。
首先打开Locale生成器配置：
```
> sudo vim /etc/locale.gen
# 这里提供了不少语言与对应编码，取消注释以下编码：
# en_US.UTF-8 UTF-8
# zh_CN.UTF-8 UTF-8
# zh_TW.UTF-8 UTF-8
> sudo locale-gen
> su -i
> echo LANG=zh_CN.utf8 > /etc/locale.conf
```

# 主机名
主机名是自己电脑的标志，在局域网中非常重要。编辑用来存放主机名的文件：
```
> sudo vim /etc/hostname
```

# 用户
[user]

# 驱动
## 显示
[xorg](../packages/xorg.md)
[dwm](../packages/dwm.md)
[kde](../packages/kde.md)
