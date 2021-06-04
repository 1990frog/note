[TOC]

# 安装fcitx5
```
> pacman -S fcitx5 fcitx5-qt fcitx5-gtk fcitx5-configtool
```
# 设置全局变量
```
> vim ~/.xprofile
export GTK_IM_MODULE=fcitx5
export QT_IM_MODULE=fcitx5
export XMODIFIERS="@im=fcitx5"

export LANG="zh_CN.UTF-8"
export LC_CTYPE="zh_CN.UTF-8"
```
# 安装rime本体
```
> pacman -S fcitx5-rime
```
# 安装四叶草
```
> yay -S rime-cloverpinyin
```
# 配置文件位置
ibus	~/.config/ibus/rime
fcitx	~/.config/fcitx/rime
fcitx5	/usr/share/rime-data/
# 安装各种词库
```
# 萌娘百科词库
> sudo pacman -S fcitx5-pinyin-moegirl-rime
# 维基百科词库
> sudo pacman -S fcitx5-pinyin-zhwiki-rime
```
# 使用sougou皮肤
https://www.fkxxyz.com/d/ssfconv2/