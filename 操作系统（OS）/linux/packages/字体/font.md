[TOC]

# 字体
## 属性
+ family 字族
+ slant 倾斜
+ weight 字重

字族就是它的名字啦。常见的指代字体的方式除了字族之外还有 Postscript 名，它不含空格、使用短横线将样式附加在名称之后，比如「DejaVuSans-BoldOblique」。后者是 CSS @font-face 规则中使用 local 时唯一指定样式的方法（除非该字体把样式也写到了字族名里）。

倾斜就是斜不斜，英文叫「Roman」「Italic」或者「Oblique」，Italic 是专门的斜体写法（更接近手写样式）， Oblique 是把常规写法倾斜一下完事。

字重就更简单了，就是笔划的粗细。常见的有 Regular、Normal、Medium、Bold、Semibold、Black、Thin、Light、Extralight 等。

# 字体管理
```
# 安装字体管理
> yay -S fontconfig

# 查看字体路径
> vim /etc/fonts/fonts.conf
```

## 目录
/usr/share/fonts

## 建立字体缓存
```
> mkfontscale
```

## 建立字体管理文件夹
```
> mkfontdir
```

## 查看安装字体
```
> fc-list
```

## 刷新字体
```
> fc-cache -fv
```

# 字体收藏
## 中英文字体带图标
+ nerd-fonts-sarasa-term
## Noto Goole字体，noto没有豆腐方块
谷歌开源字体Noto，包括中日韩字体、英文字体以及Emoji字体
+ sudo pacman -S noto-fonts: 大部分文字的常见样式，不包含汉字
+ sudo pacman -S noto-fonts-cjk: 汉字部分
+ sudo pacman -S noto-fonts-emoji: 彩色的表情符号字体
+ sudo pacman -S noto-fonts-extra: 提供额外的字重和宽度变种

## FiraCode 编程、连字
[FiraCode](https://github.com/tonsky/FiraCode)
+ sudo pacman -S ttf-fira-code

+ sudo pacman -S extra/ttf-firacode-nerd

## awesome 图标字体
[fontawesome](https://fontawesome.com.cn/)
+ sudo pacman -S ttf-font-awesome

# noto 日语问题
sudo vim /etc/fonts/conf.d/64-language-selector-prefer.conf 

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<alias>
		<family>sans-serif</family>
		<prefer>
			<family>Noto Sans CJK SC</family>
			<family>Noto Sans CJK TC</family>
			<family>Noto Sans CJK JP</family>
		</prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer>
			<family>Noto Sans Mono CJK SC</family>
			<family>Noto Sans Mono CJK TC</family>
			<family>Noto Sans Mono CJK JP</family>
		</prefer>
	</alias>
</fontconfig>