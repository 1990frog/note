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


---

# 配置文件
模糊音

# 模糊音定義先於簡拼定義，方可令簡拼支持以上模糊音
    - abbrev/^([a-z]).+$/$1/           # 簡拼（首字母）
    - abbrev/^([zcs]h).+$/$1/          # 簡拼（zh, ch, sh）

    # 以下是一組容錯拼寫，《漢語拼音》方案以前者爲正
    - derive/^([nl])ve$/$1ue/          # nve = nue, lve = lue
    - derive/^([jqxy])u/$1v/           # ju = jv,
    - derive/un$/uen/                  # gun = guen,
    - derive/ui$/uei/                  # gui = guei,
    - derive/iu$/iou/                  # jiu = jiou,

    # 自動糾正一些常見的按鍵錯誤
    - derive/([aeiou])ng$/$1gn/        # dagn => dang
    - derive/([dtngkhrzcs])o(u|ng)$/$1o/  # zho => zhong|zhou
    - derive/ong$/on/                  # zhonguo => zhong guo
    - derive/ao$/oa/                   # hoa => hao
    - derive/([iu])a(o|ng?)$/a$1$2/    # tain => tian
  
# 关闭emoji
vim /usr/share/rime-data/clover.schema.yaml
```
#emoji_suggestion:
    #  opencc_config: emoji.json
    #  option_name: emoji_suggestion
    #  tips: all
```