[TOC]

# wiki
[四叶草](https://github.com/fkxxyz/rime-cloverpinyin/wiki)
[官方模糊音](https://gist.github.com/lotem/2320943)
[FCITX5](https://wiki.archlinux.org/title/Fcitx5_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#IntelliJ_%E7%B3%BB%E5%88%97%E8%BD%AF%E4%BB%B6%E7%9A%84_IDE_%E4%B8%AD%E8%BE%93%E5%85%A5%E6%A1%86%E4%BD%8D%E7%BD%AE%E4%B8%8D%E6%AD%A3%E7%A1%AE)

# fcitx5
## 安装
```
> sudo pacman -S fcitx5 fcitx5-qt fcitx5-gtk fcitx5-configtool
```

## 配置
```
> vim ~/.pam_environment

GTK_IM_MODULE DEFAULT=fcitx
QT_IM_MODULE  DEFAULT=fcitx
XMODIFIERS    DEFAULT=@im=fcitx
INPUT_METHOD  DEFAULT=fcitx
SDL_IM_MODULE DEFAULT=fcitx

> vim ~/.xprofile
export GTK_IM_MODULE=fcitx5
export QT_IM_MODULE=fcitx5
export XMODIFIERS="@im=fcitx5"
export LANG="zh_CN.UTF-8"
export LC_CTYPE="zh_CN.UTF-8"
```

## 开机启动
```
> /usr/share/applications/org.fcitx.Fcitx5.desktop ~/.config/autostart/
```

# rime
## 安装
```
> sudo pacman -S fcitx5-rime
```

# 四叶草
## 安装
```
> yay -S rime-cloverpinyin
```

## 配置
| 方案   | 位置                 |
| ------ | -------------------- |
| ibus   | ~/.config/ibus/rime  |
| fcitx  | ~/.config/fcitx/rime |
| fcitx5 | /usr/share/rime-data |

```
> vim /usr/share/rime-data/default.custom.yaml

patch:
  "menu/page_size": 9
  schema_list:
    - schema: clover
```

## 快捷键
| 功能          | 快捷键                          |
| ------------- | ------------------------------- |
| 繁简切换      | Ctrl+Shift+2、Ctrl+Shift+f      |
| emoji开关     | Ctrl+Shift+3                    |
| 符号输入      | Ctrl+Shift+4                    |
| ascii标点切换 | Ctrl+Shift+5 、 Ctrl+, 或 Ctrl+ |
| 全半角切换    | Ctrl+Shift+6 、 Shift+Space     |

# 词库
```
# 萌娘百科词库
> sudo pacman -S fcitx5-pinyin-moegirl-rime
# 维基百科词库
> sudo pacman -S fcitx5-pinyin-zhwiki-rime
```

# 使用sougou皮肤
https://www.fkxxyz.com/d/ssfconv2/
