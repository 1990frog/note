<!-- TOC -->

- [安装](#%E5%AE%89%E8%A3%85)
- [环境变量](#%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F)
- [命令](#%E5%91%BD%E4%BB%A4)
    - [指定版本安装](#%E6%8C%87%E5%AE%9A%E7%89%88%E6%9C%AC%E5%AE%89%E8%A3%85)
    - [use](#use)
    - [ls](#ls)
- [安装yarn](#%E5%AE%89%E8%A3%85yarn)
- [默认](#%E9%BB%98%E8%AE%A4)

<!-- /TOC -->

# 安装
```
> curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```

# 环境变量
```
# vim .zshrc
# source .zshrcc

export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
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