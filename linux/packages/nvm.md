[TOC]

# 安装
```
> curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```

# 环境变量
```
# vim .zshrc
# source .zshrc

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