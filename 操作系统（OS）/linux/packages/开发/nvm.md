<!-- TOC -->

- [安装](#%E5%AE%89%E8%A3%85)
    - [yay安装](#yay%E5%AE%89%E8%A3%85)
    - [curl安装](#curl%E5%AE%89%E8%A3%85)
- [配置](#%E9%85%8D%E7%BD%AE)
- [命令](#%E5%91%BD%E4%BB%A4)
    - [指定版本安装](#%E6%8C%87%E5%AE%9A%E7%89%88%E6%9C%AC%E5%AE%89%E8%A3%85)
    - [use](#use)
    - [ls](#ls)
- [安装yarn](#%E5%AE%89%E8%A3%85yarn)
- [默认](#%E9%BB%98%E8%AE%A4)

<!-- /TOC -->

# 安装
## yay安装
yay -S nvm
source /usr/share/nvm/init-nvm.sh

## curl安装
```
> curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```

# 配置
```
> vim .zshrc
+ export NVM_DIR="$HOME/.nvm"
+ [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```

# 命令
## 指定版本安装
nvm i 14/15/16

## use
nvm use 15

## ls
nvm ls

# 安装yarn
```
> npm i install --global yarn
> sudo ln -s /home/cai/.nvm/versions/node/v15.14.0/bin/yarn /usr/bin/yarnjs
```

# 默认
nvm alias default 6.11.5