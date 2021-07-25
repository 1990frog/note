[TOC]

# wiki
[四叶草](https://github.com/fkxxyz/rime-cloverpinyin/wiki)
[官方模糊子](https://gist.github.com/lotem/2320943)

# 安装
## fcitx5
```
> sudo pacman -S fcitx5 fcitx5-qt fcitx5-gtk fcitx5-configtool
```
## rime本体
```
> sudo pacman -S fcitx5-rime
```
## 四叶草
```
> yay -S rime-cloverpinyin
```

# 配置
# 文件路径
| 方案   | 位置                 |
| ------ | -------------------- |
| ibus   | ~/.config/ibus/rime  |
| fcitx  | ~/.config/fcitx/rime |
| fcitx5 | /usr/share/rime-data |

## 四叶草
vim /usr/share/rime-data/default.custom.yaml
```
patch:
  "menu/page_size": 8
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

## 安装各种词库
```
# 萌娘百科词库
> sudo pacman -S fcitx5-pinyin-moegirl-rime
# 维基百科词库
> sudo pacman -S fcitx5-pinyin-zhwiki-rime
```

## 使用sougou皮肤
https://www.fkxxyz.com/d/ssfconv2/

## 设置全局变量
```
> vim ~/.xprofile
export GTK_IM_MODULE=fcitx5
export QT_IM_MODULE=fcitx5
export XMODIFIERS="@im=fcitx5"

export LANG="zh_CN.UTF-8"
export LC_CTYPE="zh_CN.UTF-8"
```