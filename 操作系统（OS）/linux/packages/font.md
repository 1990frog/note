<!-- TOC -->

- [字体引擎](#字体引擎)
- [安装中文字体](#安装中文字体)

<!-- /TOC -->

# 字体引擎
```
> vim /etc/profile.d/freetype2.sh
--------------------------------------------
# 取消注释最后一句
export FREETYPE_PROPERTIES="truetype:interpreter-version=40"
```

# 安装中文字体
ArchLinux默认没有中文字体，无法显示中文，必须手动安装
```
$ pacman -S noto-fonts-cjk noto-fonts noto-fonts-emoji wqy-microhei
```
以上选用谷歌开源字体Noto，包括中日韩字体、英文字体以及Emoji字体

+ adobe-source-code-pro-fonts（字体Source Code Pro）

在安装桌面环境/窗口管理器之前，也许你会先安装些美观的字体。Dejavu 是不错的字体集。英文字体优先选择dejavu字体
pacman -S ttf-dejavu


对于中文字体，开源的文泉驿正黑矢量字体是不错的选择，它还内嵌了9pt-12pt的点阵宋体：
pacman -S wqy-zenhei
pacman -S wqy-microhei


