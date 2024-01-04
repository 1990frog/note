[TOC]

[wiki](https://hyprland.org/)

# install
```
> yay -S xorg-xwayland-hidpi-xprop wlroots-hidpi-xprop-git hyprland-hidpi-xprop-git
> yay -S xorg-xrdb
```

注：xorg-xwayland-hidpi-xprop 解决 jetbrain 窗口破碎

## 高分屏缩放
```
# 告诉 wayland xwayland它自己会缩放两倍,让 wayland 不要管 xwayland 的缩放
exec-once = xprop -root -f _XWAYLAND_GLOBAL_OUTPUT_SCALE 32c -set _XWAYLAND_GLOBAL_OUTPUT_SCALE 2    

# 设置 xwayland 的 DPI 192, 一倍的 DPI 为96, 2倍即为192
exec-once = echo 'Xft.dpi:192' | xrdb -merge

# 设置 xwayland 下 gtk 的缩放，不会影响 wayland 下 gtk 的缩放
env = GDK_SCALE,2

# 设置 xwayalnd 鼠标图标的大小
env = XCURSOR_SIZE,32
```

# bar
waybar

# 文件管理
thunar

# 终端
kitty

# 通知
mako

## 主题:
-  窗口: `mojave-gtk-theme-git`
-  鼠标: `mcmojave-cursors-git`
-  图标: `mcmojave-circle-icon-theme-git`

## 默认安装:
- `swaybg`: 壁纸
- `swwww`: 动态壁纸(支持webp gif,不支持mp4)
- `nwg-look-bin`:  GTK3 设置编辑器(eg:主题设置)
- `swaylock-effects`: 屏幕锁定
- `wlroots`: Wayland合成器库
- `wlogout`: 注销菜单
- `cava`: 音频可视化
- `polkit-kde-agent`: 身份验证
- `mako`: 通知
- `grim` `slurp`: 截图
- `swappy`: 截图处理
- `wl-clipboard` `cliphist`: 剪切板管理
- `brightnessctl`: 笔记本亮度控制(台式不需要)
- `mpv`: 视频播放
- `ristretto`: 图片查看
- `pamixer`: 命令行音量控制
- `playerctl`: 命令行播放控制
- `xorg-xwayland`: 兼容x11应用
- `JetBrainsMono Nerd Font`: 状态栏图标字体
- `pipewire` `pipewire-pulse` `pipewire-alsa` `wireplumber` `pavucontrol`: 音频相关
- `xdg-user-dirs`: 创建常见用户文件夹
- `btop`: 进程查看
- `network-manager-applet`: 网络管理
- `qt5ct`: Qt5 配置工具
- `gvfs`: 虚拟文件系统
- `gvfs-mtp`: 手机mtp连接
- `ffmpegthumbs`: 解码
- `curl`: 天气脚本使用
- `jq`: JSON 处理
- `gtk4`: 兼容chrome/chromium中文输入



swaylock

udiskie