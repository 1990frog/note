[TOC]

# 安装xorg
```
> sudo pacman -S xorg xorg-server xorg-xinit
```

# 查看显卡类型
```
> lspci | grep -e VGA -e 3D
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (rev 03)
```

# 安装驱动
```
# intel 开源驱动
> sudo pacman -S xf86-video-intel

# amd 开源驱动
> sudo pacman -S xf86-video-amdgpu

# nvidia 闭源驱动
> sudo pacman -S nvidia
```

# 初始化配置文件
```
> Xorg :0 -configure
> mv ~/xorg.conf.new /etc/X11/xorg.conf
> cp /etc/X11/xinit/xinitrc ~/.xinitrc
```

# 画面撕裂
+ [AMD](https://wiki.archlinux.org/title/Ryzen_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))


# dpi
```
~/.Xresources
Xft.dpi: 180
Xft.autohint: 0
Xft.lcdfilter:  lcddefault
Xft.hintstyle:  hintfull
Xft.hinting: 1
Xft.antialias: 1
Xft.rgba: rgb
```