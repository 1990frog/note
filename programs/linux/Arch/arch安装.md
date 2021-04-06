[TOC]

# 安装系统
## 烧盘
rufus dd模式

## 磁盘分区
```
// 查看磁盘
$ fdisk -l

// 分区，设置BOOT与HOME
$ cfdisk /dev/nvme0n1

// EFI分区格式要求FAT32
$ mkfs.fat -F 32 /dev/nvme0n1p1

// 设置主分区格式EXT4
$ mkfs.ext4 /dev/nvme0n1p2
```
todo 分区格式限制

## 挂载至安装U盘
U盘是一个系统，将目标磁盘挂载并在其上安装系统，挂载目标是/mnt，它会作为我们系统安装的目标目录
```
$ mount /dev/nvme0n1p2 /mnt
$ mkdir /mnt/boot
$ mount /dev/nvme0n1p1 /mnt/boot
```

## 编辑镜像源
```
$ vim /etc/pacman.d/mirrorlist
推荐网易源
## China
Server = http://mirrors.163.com/archlinux/$repo/os/$arch
```

## 安装系统核心组件
pacstrap是pacman的一个前端
+ base：基础组件
+ linux：Linux内核
+ linux-firmware：系统固件，包含一些驱动程序
```
$pacastrap /mnt base linux linux-firmware
```

## 切换到目标系统
有的操作只能在chroot中进行，有的只能在外面进行
```
$ arch-chroot /mnt
```

## 安装sudo
arch要自己安装
```
$ pacman -S sudo vi nvim
```

## 授予sudo权限
使用visudo工具来编辑sudo的配置文件，所有能使用sudo来执行命令的用户，都应当是“wheel”这个用户组的成员。因此，我们要在wheel组的用户使用sudo
```
$ visudo
// 取消[%whell All = (All) All]的注释
```

## 创建用户
创建一个新用户，以后登录就用它，配合sudo，取代默认的root用户，提高安全性。
使用useradd来创建用户：
useradd -G wheel -m 用户名，其中-m参数代表自动创建用户的家目标。
passwd 用户名
```
$ useradd -G wheel -m [username]
$ passwd [username]
$ ls /home
```

## 安装Grub软件包
Grub软件包包含Grub启动器的安装/管理工具
用pacman在chroot环境中装上
```
$ pacman -S grub intel-ucode os-prober
```
## 安装Grub到硬盘
接下来把Grub安装到我们MBR的硬盘中
注意：最后一个参数，它是硬盘的设备节点，而不是启动分区的节点
```
$ grub-install --target = x86_64-efi /dev/sda
```
生成配置文件
Grub需要配置文件才能启动，但默认没有生成，需要我们自己来生成
```
$ grub-mkconfig -o /boot/grub/grub.cfg
```

old解决方案
```
$ grub-mkconfig > /boot/grub/grub.cfg
$ grub-install --target = x86_64-efi --efi-directory = /boot
```

## 生成fstab
fstab是自动挂载文件系统不可或缺的文件，缺少则无法启动。
首先exit，退出chroot环境
然后在咱环境里运行：
```
genfstab /mnt > /mnt/etc/fstab
```
最后可检验一下目标系统中生成得到的fstab

## 安装Xorg图形服务器
Linux发行版的图形界面是以Xorg作为后端来实现的
使用pacstrap来安装Xorg
```
$ pacstrap /mnt Xorg
```

## 安装网络组件
Arch linux的网络组件也需要手动安装，而不是自带。
相应的组件包括：
+ dhcpcd：DHCP客户端
+ wpa_supplicant：WLAN功能
+ networkmanager：网络管理前段工具，被KDE等桌面使用
```
$ pacman -S dhcpcd wpa_supplicant networkmanager
```
## 启用网络组件
要使网络组件生效，还需要启动。
首先用arch-chroot切换到目标系统中
```
$ systemctl enable dhcpcd
$ systemctl enable wpa_supplicant
$ systemctl enable networkmanager
```

## 安装音频组件（todo 蓝牙）
```
$ pacstrap /mnt alsa-utils pulseaudio pulseaudio-alsa
```
KDE使用PulseAudio作为音频后端，而PulseAudio的后端则是ALSA

## 安装KDE Plasma
Plasma是KDE的桌面环境，也是它的本体。运行以下命令安装
```
$ pacstrap /mnt plasma-meta sddm
```
而plasma-meta安装所有核心组件，而sddm是窗口管理器，用来在Xorg环境下显示图形登录界面，并启动Plasma。
## 启动SDDM
SDDM是一个桌面管理器，KDE的登录界面就是由它显示的，登录后也由它负责启动Plasma。
arch-chroot切换到目标系统，然后启用它
```
$ systemctl enable sddm
```

第一阶段OK

## 安装KDE组件
KDE的所有APP均可按需采用。如果有兴趣，你也可以安装特定分类的应用，或者是——直接上全家桶！
```
$ sudo pacman -S kde-applications-meta
```
还可以通过以下命令来获取KDE家族的其他应用列表
```
$ sudo pacman -S kde-applications
```
### 删除用不到的app
```
sudo pacman -R kde-games
sudo pacman -R blinken kanagram khangman
sudo pacman -R kde-utilities-meta
sudo pacman -R kde-utilitie
sudo pacman -R kde-education-meta
sudo pacman -R kde-education
```

## 安装中文字体
ArchLinux默认没有中文字体，无法显示中文，必须手动安装
```
$ pacman -S noto-fonts-cjk
$ pacman -S noto-fonts
$ pacman -S noto-fonts-emoji
$ pacman -S wqy-microhei
```
以上选用谷歌开源字体Noto，包括中日韩字体、英文字体以及Emoji字体

## 本地化
Locale数据，用于控制操作系统的本地化，以支持不同的语音、时间格式等。
首先打开Locale生成器配置：
```
$ sudo vim /etc/locale.gen
这里提供了不少语言与对应编码，取消注释以下编码：
en_US.UTF-8 UTF-8
zh_CN.UTF-8 UTF-8
zh_TW.UTF-8 UTF-8
```
中文支持的基础就是locale，但系统不会默认生成，仍需手动生成。

生成Locale
```
sudo locale-gen
```
将语言设置为中文：
```
export LANG=zh_CN.utf8
```
然后尝试运行一些带中文的命令，看看能否正常显示中文。

例如：
ls --help

设置默认Locale
一般把默认Locale设为英文，便于调试，且不容易有乱码。
先用`sudo -i`切换到root，然后运行
```
echo LANG=zh_CN.utf8 > /etc/locale.conf
```
最后用exit命令返回

## 设置KDE中文
在区域中，设置“Formats”为中文

## 设置主机名
主机名是自己电脑的标志，在局域网中非常重要。编辑用来存放主机名的文件：
```
sudo vim /etc/hostname
```
## 设置root密码
理论上有了sudo，我们就不必再用root账号了。但这并不表示绝对安全，因为TTY模式下还能输入root账号名来登录root账号，而且默认是没有密码的！
更重要的是，访客也可以通过ssh等来直接登录！
```
$ sudo -i
$ passwd
```

## 设置ArchLinuxCN
archlinuxcn是由国人社区维护的一个Arch LInux软件源，包含了不少不被官方包含的软件、库等，尤其是国人原创的。
```
$ sudo vim /etc/pacman.conf
[archlinuxcn]
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
```
更新软件仓库
```
$ sudo pacman -Sy
```
要想使用archlinuxcn，还需要安装密钥环
```
sudo pacman -S archlinuxcn-keyring
```
如果密钥报错【GnuPG-2.1 与 pacman 密钥环】
由于升级到了 gnupg-2.1，pacman 上游更新了密钥环的格式，这使得本地的主密钥无法签署其它密钥。这不会出问题，除非你想自定义 pacman 密钥环。不过，我们推荐所有用户都生成一个新的密钥环以解决潜在问题。
此外，我们建议您安装 haveged，这是一个用来生成系统熵值的守护进程，它能加快加密软件（如 gnupg，包括生成新的密钥环）关键操作的速度。
要完成这些操作，请以 root 权限运行：
```
$ pacman -Syu haveged
$ systemctl start haveged
$ systemctl enable haveged

$ rm -fr /etc/pacman.d/gnupg
$ pacman-key --init
$ pacman-key --populate archlinux
$ pacman-key --populate archlinuxcn
```

## 引导
```
$ pacman -S grub efibootmgr intel-ucode os-prober
$ grub-mkconfig > /boot/grub/grub.cfg
$ grub-install --target = X86_64-efi --efi-directory = /boot
```

# 常用软件
## 蓝牙
### 安装蓝牙
### win10、arch蓝牙同步
http://bluetoothinstaller.com/bluetooth-command-line-tools/



# 常用软件
## sougou拼音
```
$ sudo pacman -S fcitx fcitx-rime fcitx-im kcm-fcitx fcitx-sogoupinyin
```
配置输入法
```
$ vim ~/.xprofile
export LANG=zh_CN.UTF-8
export LC_ALL=zh_CN.UTF-8
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"
```
## openssh
## base-devel
## xf86-video-intel
## ntfs-3g
## net-tools
## refind
## lolcat
## proxychains
## flameshot
## neofetch
## yay -S aur/dingtalk-electron
## thefuck
## reflector
首先安装reflector工具
```
$ sudo pacman -S reflector
```
然后执行
```
$ sudo reflector --sort rate --threads 100 -c China --save /etc/pacman.d/mirrorlist
```
最终生成的mirrorlist如下面的样子
```
Server = http://mirrors.163.com/archlinux/$repo/os/$arch
Server = https://mirrors.dgut.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.nju.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.bfsu.edu.cn/archlinux/$repo/os/$arch
Server = http://mirrors.bfsu.edu.cn/archlinux/$repo/os/$arch
Server = http://mirrors.zju.edu.cn/archlinux/$repo/os/$arch
Server = http://mirrors.nju.edu.cn/archlinux/$repo/os/$arch
Server = http://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.sjtug.sjtu.edu.cn/archlinux/$repo/os/$arch
Server = http://mirrors.dgut.edu.cn/archlinux/$repo/os/$arch
Server = rsync://mirrors.bfsu.edu.cn/archlinux/$repo/os/$arch
```
## bashtop
## zeal
## Ranger
## Lazygit


# 蓝牙
```
sudo pacman -S bluez
sudo pacman -S bluez-utils
sudo pacman -Ss pulseaudio-bluetooth
systemctl start bluetooth
systemctl enable bluetooth

sudo nvim /etc/bluetooth/main.conf

sudo pacman -S pulseaudio-modules-bt
```


sudo pacman -S fcitx
sudo pacman -S fcitx-im
sudo pacman -S fcitx-configtool
sudo pacman -S fcitx-gtk3 fcitx-gtk4 fcitx-qt4 fcitx-qt5
yay -S fcitx-sogoupinyin

sudo pacman -S base-devel




sudo pacman -S libappimage




sudo pacman -Ss electronic-wechat