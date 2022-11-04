<!-- TOC -->

- [wiki](#wiki)
- [安装xorg](#安装xorg)
- [查看显卡类型](#查看显卡类型)
- [安装驱动](#安装驱动)
- [初始化配置文件](#初始化配置文件)
- [画面撕裂](#画面撕裂)
- [dpi](#dpi)

<!-- /TOC -->

# wiki
[wiki](https://wiki.archlinux.org/title/Xorg_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

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

```
> vim /etc/X11/xorg.conf
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "Accel"                     # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "EnablePageFlip"            # [<bool>]
        #Option     "SubPixelOrder"             # [<str>]
        #Option     "ZaphodHeads"               # <str>
        #Option     "AccelMethod"               # <str>
        #Option     "DRI3"                      # [<bool>]
        #Option     "DRI"                       # <i>
        #Option     "ShadowPrimary"             # [<bool>]
        #Option     "TearFree"                  # [<bool>]
        #Option     "DeleteUnusedDP12Displays"  # [<bool>]
        #Option     "VariableRefresh"           # [<bool>]
        #Option     "AsyncFlipSecondaries"      # [<bool>]
        Identifier  "Card0"
        Driver      "amdgpu"
+       Option "TearFree" "true"
        BusID       "PCI:43:0:0"
EndSection
```

# dpi
```
~/.Xresources
Xft.dpi: 157
Xft.autohint: 0
Xft.lcdfilter:  lcddefault
Xft.hintstyle:  hintfull
Xft.hinting: 1
Xft.antialias: 1
Xft.rgba: rgb
```