[TOC]

# KDB
## 安装KDE Plasma
Plasma是KDE的桌面环境，也是它的本体。运行以下命令安装
```
> pacman -S plasma-meta
```

## 安装SDDM
SDDM是一个桌面管理器，用来在Xorg环境下显示图形登录界面，并启动Plasma。
KDE的登录界面就是由它显示的，登录后也由它负责启动Plasma。
```
> pacman -S sddm
> systemctl enable sddm
```

## 安装KDE全家桶
KDE的所有APP均可按需采用。如果有兴趣，你也可以安装特定分类的应用，或者是——直接上全家桶！
```
> sudo pacman -S kde-applications-meta
```
还可以通过以下命令来获取KDE家族的其他应用列表
```
> sudo pacman -S kde-applications
```

## 删除用不到的app
```
> sudo pacman -R kde-games
> sudo pacman -R blinken kanagram khangman
> sudo pacman -R kde-utilities-meta
> sudo pacman -R kde-utilitie
> sudo pacman -R kde-education-meta
> sudo pacman -R kde-education
```

## 音频
### 声音服务
KDE使用PulseAudio作为音频后端，而PulseAudio的后端则是ALSA
```
$ pacstrap /mnt alsa-utils pulseaudio pulseaudio-alsa
```
### 蓝牙音频
```
$ sudo pacman -S pulseaudio-modules-bt
```