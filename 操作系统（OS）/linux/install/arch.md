[TOC]

# 安装镜像
[download](https://archlinux.org/download/)
[163](https://mirrors.163.com/archlinux/iso/)

# 创建启动盘
[rufus](https://rufus.ie/zh/)
使用 dd 模式烧盘

# archinstall
[archinstall](https://wiki.archlinuxcn.org/wiki/Archinstall?rdfrom=https%3A%2F%2Fwiki.archlinux.org%2Findex.php%3Ftitle%3DArchinstall_%28%25E7%25AE%2580%25E4%25BD%2593%25E4%25B8%25AD%25E6%2596%2587%29%26redirect%3Dno)

## 命令
```
> archinstall
```

## 不足
不支持rEFInd引导

# 传统安装方式（推荐）
[wiki](https://wiki.archlinuxcn.org/wiki/%E5%AE%89%E8%A3%85%E6%8C%87%E5%8D%97)

## 分区
```shell
# 查看磁盘
> lsblk

# cfdisk分区
> cfdisk /dev/磁盘
/boot fat32 1GB
/     ext4  全部

# 格式化
# 设置主分区格式EXT4  
> mkfs.ext4 /dev/root_partition（根分区）
# EFI分区格式要求FAT32  
> mkfs.fat -F 32 /dev/efi_system_partition（EFI 系统分区）
# 交换分区
> mkswap /dev/swap_partition（交换空间分区）

# 将根磁盘卷挂载到 /mnt
> mount /dev/root_partition（根分区） /mnt
# 对于 UEFI 系统，挂载 EFI 系统分区
> mount --mkdir /dev/efi_system_partition（EFI 系统分区） /mnt/boot
# 如果创建了交换空间卷，请使用 swapon 启用它
> swapon /dev/swap_partition（交换空间分区）
```

## 安装包
```shell
> pacstrap -K /mnt 
    base \
    base-devel \
    linux-zen \
    linux-zen-headers \
    linux-firmware \
    dhcpcd \
    iwd \
    refind \
    neovim \
    git
    amd-ucode or intel-ucode
```
+ linux 内核
+ linux-firmware 硬件驱动
+ base 基本的用户工具
+ base-devel 基础的开发工具
+ neovim 编辑器
+ [dhcpcd](../packages/网络/dhcpcd.md) 有线网卡
+ [iwd](../packages/网络/iwd.md) 无线网卡
+ amd-ucode 微码


## 生成fstab文件
```
> genfstab -U /mnt >> /mnt/etc/fstab
```

## chroot到新安装的系统
```
> arch-chroot /mnt
```

## 设置时区
[系统时间](https://wiki.archlinuxcn.org/wiki/%E7%B3%BB%E7%BB%9F%E6%97%B6%E9%97%B4)
```
> ln -sf /usr/share/zoneinfo/Asia/Chongqing /etc/localtime
```

## 区域和本地化设置
[Locale](https://wiki.archlinuxcn.org/wiki/Locale)
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

## 创建hostname
```
> vim /etc/hostname
hostname（主机名）
```

## 创建用户
``` shell
> ln -s /usr/bin/nvim /usr/bin/vim
> pacman -S sudo
> visudo
# 取消[%whell All = (All) All]的注释

> sudo -i
> passwd

> useradd -G wheel -m [username]
> passwd [username]
> ls /home
```

## 引导
```
> refind-install
> vim -O /boot/refind_linux.conf /etc/fstab

"Boot with standard options"  "ro root=UUID=0e4c6521-123b-4a81-b328-26537a6f88ee splash=silent quiet showopts"
"Boot to single-user mode"    "ro root=UUID=0e4c6521-123b-4a81-b328-26537a6f88ee splash=silent quiet showopts single"
"Boot with minimal options"   "ro root=UUID=0e4c6521-123b-4a81-b328-26537a6f88ee"
```

## archlinuxcn
```shell
> sudo vim /etc/pacman.conf
//在最后添加
[archlinuxcn]
SigLevel = Optional TrussAll
Server = https://mirrors.sjtug.sjtu.edu.cn/archlinux-cn/$arch
//顺便找到这一行，取消注释
[multilib]
Include = /etc/pacman.d/mirrorlist

> sudo pacman -Sy archlinuxcn-keyring
> sudo pacman -S yay
```

## 网络驱动
```shell
> systemctl enable --now dhcpcd
> systemctl enable --now iwd
> sudo pacman -S plasma-nm
> systemctl enable --now NetworkManager
```

## 蓝牙驱动
```shell
# blueman方案
> yay -S bluez bluez-utils blueman
> systemctl enable --now bluetooth

# KDE方案
>  sudo pacman -S bluedevil
```

## 声卡u驱动
```shell
> sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack wireplumber
> systemctl --user enable --now pipewire.socket
> systemctl --user enable --now pipewire-pulse.socket
> systemctl --user enable --now wireplumber.service
```

## 桌面
KDE
```shell
> sudo pacman -S plasma
> startplasma-wayland
```