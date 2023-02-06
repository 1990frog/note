[TOC]
# 仓库配置
## 配置
### 显示当前的git配置
git config --list
### 编辑git配置文件[全局]
git config -e [--global]
### 设置提交用户信息
git config [--global] user.name "[name]"
git config [--global] user.email "[email address]"
### 添加远程仓库地址
git remote add origin [远程仓库地址]
### 修改远程仓库地址
git remote set-url origin [远程仓库地址]


# 查看状态
## 查看工作目录和暂存区的状态
git status
4种状态：
+ untracked（未被跟踪的）：此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged.
+ Unmodify（文件已经入库）：文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为Modified. 如果使用git rm移出版本库, 则成为Untracked文件
+ Modified（文件已修改）：文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态, 使用git checkout 则丢弃修改过, 返回到unmodify状态, 这个git checkout即从库中取出文件, 覆盖当前修改
+ Staged（暂存状态）：执行git commit则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态. 执行git reset HEAD filename取消暂存, 文件状态为Modified

## 查看本地代码变化状态（add操作之前）




# 配置
## 显示当前的git配置
git config --list
## 编辑git配置文件
git config -e [--global]
## 设置提交用户信息
git config [--global] user.name "[name]"
git config [--global] user.email "[email address]"


# 删除
## 删除工作区文件，并且将这次删除放入暂存区
git rm [file1] [file2] ...
## 停止追踪指定文件，单该文件会保留在工作区
git rm --cache [file]

# 修改文件名
git mv [file-original] [file-renamed]
