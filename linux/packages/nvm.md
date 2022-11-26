<!-- TOC -->

- [安装](#安装)
- [环境变量](#环境变量)
- [命令](#命令)
  - [指定版本安装](#指定版本安装)
  - [use](#use)
  - [ls](#ls)
- [安装yarn](#安装yarn)
- [默认](#默认)

<!-- /TOC -->

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
nvm i 14/15z/16

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