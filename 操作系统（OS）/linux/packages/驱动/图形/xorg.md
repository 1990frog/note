<!-- TOC -->

- [wiki](#wiki)
- [安装xorg](#%E5%AE%89%E8%A3%85xorg)
- [查看显卡类型](#%E6%9F%A5%E7%9C%8B%E6%98%BE%E5%8D%A1%E7%B1%BB%E5%9E%8B)
- [安装驱动](#%E5%AE%89%E8%A3%85%E9%A9%B1%E5%8A%A8)
- [初始化配置文件](#%E5%88%9D%E5%A7%8B%E5%8C%96%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)
- [画面撕裂](#%E7%94%BB%E9%9D%A2%E6%92%95%E8%A3%82)
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