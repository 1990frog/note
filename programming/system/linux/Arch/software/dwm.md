[TOC]

# 必备
+ compton，picom（透明）
+ feh（背景）
+ slock（锁屏）
+ dmenu（快速启动）
+ xbacklight（调节亮度）
+ acpilight（intel集显调整亮度）
+ adobe-source-code-pro-fonts（字体Source Code Pro）
+ nerd-fonts-complete（字体Sauce Code Pro Nerd Font Mono）

# 下载
压缩包
+ [dwm](https://dl.suckless.org/dwm/dwm-6.2.tar.gz)
+ [st](https://dl.suckless.org/st/st-0.8.4.tar.gz)
+ [dmenu](https://dl.suckless.org/tools/dmenu-5.0.tar.gz)
+ [slock](https://dl.suckless.org/tools/slock-1.4.tar.gz)

git版本
+ git://git.suckless.org/dwm
+ git://git.suckless.org/st
+ git://git.suckless.org/dmenu

# 安装
## 解压
```
> tar zxvf xxx.tar.gz
> cd 目录
> make
> make clean install
```
## 打补丁
```
> patch < xx.diff
```
部分补丁需要安装rej文件修改
## 移除补丁
```
> patch -R > xx.diff
```

# 补丁
## dwm
+ dwm-cfacts-vanitygaps-6.2_combo.diff（边距）
+ dwm-fixborders-6.2.diff（透明）
+ dwm-alpha-20201019-61bb8b2.diff（透明）
+ dwm-autostart-20210120-cb3f58a.diff（自动启动脚本）
+ dwm-awesomebar-statuscmd-signal-6.2.diff（标题title）
+ dwm-hide_vacant_tags-6.2.diff（只显示开启的tag）   
+ dwm-fullscreen-6.2.diff（真全屏）   
+ dwm-scratchpad-20170207-bb3bd6f.diff（小窗口）   

# st
+ st-scrollback-0.8.4.diff（键盘行回滚）
+ st-scrollback-mouse-20191024-a2c479c.diff（鼠标行回滚）
+ st-alpha-0.8.2.diff（透明）
+ st-anygeometry-0.8.1.diff（透明）
+ st-blinking_cursor-20200531-a2a7044.diff（光标闪动）
+ st-dynamic-cursor-color-0.8.4.diff（光标背景色）
+ st-dracula-0.8.2.diff（德古拉主题）

# slock
+ slock-blur_pixelated_screen-1.4.diff（像素锁屏）

# emoji
yay -S libxft-bgra

# java支持
```
> sudo pacman -S wmname
> vim ~/.xinitrc
export _JAVA_AWT_WM_NONREPARENTING=1
export AWT_TOOLKIT=MToolkit
wmname LG3D
```

# .xinitrc 文件
```
picom &
fcitx5 &
feh --recursive --randomize --bg-fill ~/Pictures/wallpaper/wallhaven-w8yy6p.png &
export _JAVA_AWT_WM_NONREPARENTING=1
export AWT_TOOLKIT=MToolkit
wmname LG3D

exec dwm
```

# sddm 登录管理器
```
> vim /usr/share/xsessions/dwm.desktop

[Desktop Entry]
Name=dwm
Comment=Dynmic Window Manager
Exec=/usr/local/bin/dwm
TryExec=/usr/local/bin/dwm
Icon=/home/cai/Code/dwm/dwm.png
Type=Application
```

# script
```
static const char *dmenucmd[] = { "dmenu_run", "-m", dmenumon, "-fn", dmenufont, "-nb", col_gray1, "-nf", col_gray3, "-sb", col_cyan, "-sf", col_gray4, NULL };   #定义dmenu的快捷键功能
static const char *termcmd[]  = { "alacritty", NULL };   #定义alacritty终端的快捷键功能
static const char *volup[] = { "amixer", "-qM", "set", "Master", "2%+", "umute", NULL };
static const char *voldown[] = { "amixer", "-qM", "set", "Master", "2%-", "umute", NULL };   #定义系统音量大小调节的快捷键功能
static const char *mute[] = { "amixer", "-qM", "set", "Master", "toggle", NULL };   #定义开/关静音的快捷键功能
static const char *lightup[] = { "xbacklight", "-inc", "2", NULL };
static const char *lightdown[] = { "xbacklight", "-dec", "2", NULL };   #定义屏幕亮度调节的快捷键功能
static const char *chromium[]  = { "chromium", "--disk-cache-dir=/tmp/chromium", NULL };   #定义chromium浏览器的快捷键功能
static const char *dolphin[]  = { "dolphin", NULL };   #定义dolphin文件管理器的快捷键功能
```

# dmenu更换rofi
```
> vim config.def.h
- static const char *dmenucmd[] = { "demnu", NULL };
+ static const char *dmenucmd[] = { "rofi", "-show", "drun", NULL };

> vim dwm.c
void
spawn(const Arg *arg)
{
-        //if (arg->v == dmenucmd)
+        dmenumon[0] = '0' + selmon->num;
```

# key
单个按键像Fn或者多媒体键必须要用16进制数来表示，可以用xev程序来获得。或者查看 /usr/include/X11/XF86keysym.h 中的定义。
```
{ 0,                 0xff00,    spawn,       {.v = <keybindname> } }
```

# 退出