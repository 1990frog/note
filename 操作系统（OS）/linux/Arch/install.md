[TOC]

# wiki
[General recommendations](https://wiki.archlinux.org/title/General_recommendations_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
[引导](https://wiki.archlinux.org/title/Arch_boot_process_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
[多媒体](https://wiki.archlinux.org/title/Category:Multimedia_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
[核心工具](https://wiki.archlinux.org/title/Core_utilities_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
[archinstall](https://wiki.archlinuxcn.org/wiki/Archinstall)

# 烧盘
+ [下载](https://archlinux.org/download/)
+ rufus dd模式烧盘


# 安装

## archinstall
简单是简单，但是不能设置refind引导

## 传统安装
### 分盘
[cfdisk](../packages/cfdisk.md)
[gdisk](../packages/gdisk.md)

格式化
```shell
# EFI分区格式要求FAT32  
> mkfs.fat -F 32 /dev/nvme0n1p1  
# 设置主分区格式EXT4  
> mkfs.ext4 /dev/nvme0n1p2
```

### 



# archinstall
# 常规安装
## 磁盘
### 分区
[xdisk](../packages/xdisk.md)  
分两个区：

+ root
+ home

### 挂载
```
> mkdir /mnt/boot
> mount /dev/nvme0n1p1 /mnt/boot
> mount /dev/nvme0n1p2 /mnt
```

## 安装linux
### 安装软件仓库源
[reflector](../packages/reflector.md)
[pacman](../packages/pacman.md)

### 安装
```
> pacstrap /mnt linux-zen linux-zen-header linux-firmware base base-devel neovim dhcpcd iwd amd-ucode
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

## 挂载
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

## 声音

## 网络



-----

双系统系统时间同步
输入以下指令，使 linux 不修改 bios 时间

timedatectl set-local-rtc 1 --adjust-sy



# 编辑环境变量
http_proxy=http://127.0.0.1:7890/
https_proxy=http://127.0.0.1:7890/
ftp_proxy=http://127.0.0.1:7890/
HTTP_PROXY=http://127.0.0.1:7890/
HTTPS_PROXY=http://127.0.0.1:7890/
FTP_PROXY=http://127.0.0.1:7890/


# 安装蓝牙
安装蓝牙模块。

sudo pacman -S bluez
设置开机启动。

systemctl enable bluetooth
systemctl start blutooth
安装蓝牙音频。

sudo pacman -S pluseaudio-bluetooth

修改 system.pa。

sudo vim /etc/pulse/system.pa
写入以下内容。

load-module module-bluetooth-policy
load-module module-bluetooth-discover