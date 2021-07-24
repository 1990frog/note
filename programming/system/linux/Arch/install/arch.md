[TOC]

# 前期准备
+ [下载](https://archlinux.org/download/)
+ rufus dd模式烧盘

# 分区
查看磁盘
```
> lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme0n1      8:0    0 1000G  0 disk
```
格式化
[xdisk]

# 挂载
```
> mount /dev/nvme0n1p2 /mnt
> mkdir /mnt/boot
> mount /dev/nvme0n1p1 /mnt/boot
```

# 安装linux
## 找源
[reflector]
## 安装
```
> pacstrap /mnt base linux linux-firmware
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

# 进入系统
```
> arch-chroot /mnt
```

# 显示
[xorg]

# 设置时区
```
> ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
> hwclock --systohc
```
坑：双系统UTC与local

# 主机名
主机名是自己电脑的标志，在局域网中非常重要。编辑用来存放主机名的文件：
```
> sudo vim /etc/hostname
```

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

