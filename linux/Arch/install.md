<!-- TOC -->

- [wiki](#wiki)
- [前期准备](#%E5%89%8D%E6%9C%9F%E5%87%86%E5%A4%87)
- [驱动](#%E9%A9%B1%E5%8A%A8)
- [磁盘](#%E7%A3%81%E7%9B%98)
    - [分区](#%E5%88%86%E5%8C%BA)
    - [挂载](#%E6%8C%82%E8%BD%BD)
- [安装linux](#%E5%AE%89%E8%A3%85linux)
    - [安装软件仓库源](#%E5%AE%89%E8%A3%85%E8%BD%AF%E4%BB%B6%E4%BB%93%E5%BA%93%E6%BA%90)
    - [安装](#%E5%AE%89%E8%A3%85)
- [挂载](#%E6%8C%82%E8%BD%BD)
- [启动器](#%E5%90%AF%E5%8A%A8%E5%99%A8)
- [Chroot](#chroot)
- [显示](#%E6%98%BE%E7%A4%BA)
- [设置时区](#%E8%AE%BE%E7%BD%AE%E6%97%B6%E5%8C%BA)
- [本地化](#%E6%9C%AC%E5%9C%B0%E5%8C%96)
- [主机名](#%E4%B8%BB%E6%9C%BA%E5%90%8D)
- [用户](#%E7%94%A8%E6%88%B7)

<!-- /TOC -->

# wiki
[General recommendations](https://wiki.archlinux.org/title/General_recommendations_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
[引导](https://wiki.archlinux.org/title/Arch_boot_process_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
[多媒体](https://wiki.archlinux.org/title/Category:Multimedia_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
[核心工具](https://wiki.archlinux.org/title/Core_utilities_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

# 前期准备
+ [下载](https://archlinux.org/download/)
+ rufus dd模式烧盘

# 驱动


# 磁盘
## 分区
查看磁盘
```
> lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme0n1      8:0    0 1000G  0 disk
```
格式化
[xdisk]

## 挂载
```
> mount /dev/nvme0n1p2 /mnt
> mkdir /mnt/boot
> mount /dev/nvme0n1p1 /mnt/boot
```

# 安装linux
## 安装软件仓库源
[reflector]
## 安装
```
> pacstrap /mnt base linux linux-firmware base-devel
```
切记安装网络
[dhcpcd]
[iwd]

# 挂载
uuid模式：`-U`，默认目录模式
```
> genfstab -U /mnt >> /mnt/etc/fstab
```

# 启动器
+ [refind]
+ [bootctl]
+ [grub]

# Chroot
```
> arch-chroot /mnt
```

# 显示
[xorg]
[dwm]
[kde]

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