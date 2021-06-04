[TOC]

# 安装zsh
```
> sudo pacman -S zsh
```
# 安装oh-my-zsh
```
> sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
# 配置文件
``` conf
plugins=(git
        git-auto-fetch
        zsh-autosuggestions
        zsh-syntax-highlighting
        autojump
        gitignore
        cp
        zsh_reload
        z
        vi-mode
        command-not-found
        safe-paste
        colored-man-pages
        sudo
)
```