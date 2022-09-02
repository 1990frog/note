<!-- TOC -->

- [wiki](#wiki)
- [安装（fcitx5、rime、clover）](#%E5%AE%89%E8%A3%85fcitx5rimeclover)
- [配置](#%E9%85%8D%E7%BD%AE)
    - [linux 环境](#linux-%E7%8E%AF%E5%A2%83)
    - [开机启动](#%E5%BC%80%E6%9C%BA%E5%90%AF%E5%8A%A8)
    - [词库、配置文件目录](#%E8%AF%8D%E5%BA%93%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6%E7%9B%AE%E5%BD%95)
    - [启用四叶草](#%E5%90%AF%E7%94%A8%E5%9B%9B%E5%8F%B6%E8%8D%89)
    - [模糊音](#%E6%A8%A1%E7%B3%8A%E9%9F%B3)
    - [关闭emoji](#%E5%85%B3%E9%97%ADemoji)
- [快捷键](#%E5%BF%AB%E6%8D%B7%E9%94%AE)
- [词库](#%E8%AF%8D%E5%BA%93)
    - [转换工具](#%E8%BD%AC%E6%8D%A2%E5%B7%A5%E5%85%B7)
    - [格式](#%E6%A0%BC%E5%BC%8F)
    - [四叶草配置词库](#%E5%9B%9B%E5%8F%B6%E8%8D%89%E9%85%8D%E7%BD%AE%E8%AF%8D%E5%BA%93)
- [使用sougou皮肤](#%E4%BD%BF%E7%94%A8sougou%E7%9A%AE%E8%82%A4)

<!-- /TOC -->

# wiki
[四叶草](https://github.com/fkxxyz/rime-cloverpinyin/wiki)
[官方模糊音](https://gist.github.com/lotem/2320943)
[FCITX5](https://wiki.archlinux.org/title/Fcitx5_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#IntelliJ_%E7%B3%BB%E5%88%97%E8%BD%AF%E4%BB%B6%E7%9A%84_IDE_%E4%B8%AD%E8%BE%93%E5%85%A5%E6%A1%86%E4%BD%8D%E7%BD%AE%E4%B8%8D%E6%AD%A3%E7%A1%AE)


https://github.com/fkxxyz/rime-cloverpinyin/wiki/linux#%E5%9F%BA%E4%BA%8Efcitx5

# 安装（fcitx5、rime、clover）
fcitx5
> sudo pacman -S fcitx5 fcitx5-qt fcitx5-gtk fcitx5-configtool

rime
> sudo pacman -S fcitx5-rime

clover
> sudo pacman -S rime-cloverpinyin

# 配置
## linux 环境
```
> vim ~/.xprofile
export GTK_IM_MODULE=fcitx5
export QT_IM_MODULE=fcitx5
export XMODIFIERS="@im=fcitx5"
export LANG="zh_CN.UTF-8"
export LC_CTYPE="zh_CN.UTF-8"
```

## 开机启动
```
> sudo cp /usr/share/applications/org.fcitx.Fcitx5.desktop ~/.config/autostart/
```

## 词库、配置文件目录
| 方案   | 位置                 |
| ------ | -------------------- |
| ibus   | ~/.config/ibus/rime  |
| fcitx  | ~/.config/fcitx/rime |
| fcitx5 | /usr/share/rime-data |

## 启用四叶草
```
> vim /usr/share/rime-data/default.custom.yaml
patch:
  "menu/page_size": 9
  schema_list:
    - schema: clover
```

## 模糊音
```
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
```
  
## 关闭emoji
```
> vim /usr/share/rime-data/clover.schema.yaml
#emoji_suggestion:
    #  opencc_config: emoji.json
    #  option_name: emoji_suggestion
    #  tips: all
```

# 快捷键
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

## 转换工具
[imewlconverter 词库转换工具](https://github.com/studyzy/imewlconverter)
## 格式
```
> vim xxx.dict.yaml
---
name: moegirl
version: "0.1"
sort: by_weight
...
柳凪    liu zhi
黑色过膝袜      hei se guo xi wa
光芒周期        guang mang zhou qi
泉田圭吾        quan tian gui wu
```
## 四叶草配置词库
```
> vim clover.dict.yaml

name: clover
version: "1"
sort: by_weight

import_tables:
  - clover.base
  - clover.phrase
  - THUOCL_animal
  - THUOCL_caijing
  - THUOCL_car
  - THUOCL_chengyu
  - THUOCL_diming
  - THUOCL_food
  - THUOCL_IT
  - THUOCL_law
  - THUOCL_lishimingren
  - THUOCL_medical
  - THUOCL_poem
  - sogou_new_words
  - moegirl
  - zhwiki
  - chengxuyuan
  - chengyu
  - falv
  - fengjingmingsheng
  - jisuanji
```

# 使用sougou皮肤
https://www.fkxxyz.com/d/ssfconv2/
