[TOC]

# 安装zsh
```
> sudo pacman -S zsh
```

# 安装oh-my-zsh
```
> sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

# 插件
https://github.com/zsh-users

+ git 命令缩写
+ z 跳转
+ zsh-syntax-highlighting 高亮
+ zsh-autosuggestions 补全
+ git-open 打开当前仓库页面
+ gitignore 查询gitignore模板
+ zsh_reload 使用src命令重载zsh
+ vi-mode vim模式
+ command-not-found 当你输入一条不存在的命令时，会自动查询这条命令可以如何获得
+ safe-paste 当你往 zsh 粘贴脚本时，它不会被立刻运行
+ sudo 双击Esc自动加sudo
+ hitokoto 一言

## git
+ gaa = git add --all
+ gcmsg = git commit -m
+ ga = git add
+ gst = git status
+ gp = git push

## git-open
git clone https://github.com/paulirish/git-open.git $ZSH_CUSTOM/plugins/git-open
