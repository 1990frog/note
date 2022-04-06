[TOC]

# git安装
# git结构
1 工作区（Working Directory）
2 版本库（repository）
2.1 暂存区（stage/index）
2.2 master

# git文件4种状态
+ untracked（未被跟踪的）：此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged.
+ Unmodify（文件已经入库）：文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为Modified. 如果使用git rm移出版本库, 则成为Untracked文件
+ Modified（文件已修改）：文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态, 使用git checkout 则丢弃修改过, 返回到unmodify状态, 这个git checkout即从库中取出文件, 覆盖当前修改
+ Staged（暂存状态）：执行git commit则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态. 执行git reset HEAD filename取消暂存, 文件状态为Modified

# 初始化
初始化git仓库,创建.git文件夹
## 在当前目录新建一个git代码块
git init 
## 新建一个目录，将其初始化为git代码库
git init [project-name]

# 配置
## 显示当前的git配置
git config --list
## 编辑git配置文件
git config -e [--global]
## 设置提交用户信息
git config [--global] user.name "[name]"
git config [--global] user.email "[email address]"

# 增加（暂存区）
## 添加指定文件到暂存区
git add [file1] [file2] ...
## 将工作空间下所有文件添加暂存区（new、modifyed）
git add .
## 将工作空间下所有文件添加到暂存区（new、modifyed、delete）
git add -A
## 将工作空间下所有文件添加到暂存区（modifyed、delete）
git add -u

# 删除
## 删除工作区文件，并且将这次删除放入暂存区
git rm [file1] [file2] ...
## 停止追踪指定文件，单该文件会保留在工作区
git rm --cache [file]

# 修改文件名
git mv [file-original] [file-renamed]

# 提交
## 提交暂存区到仓库区
git commit -m [message]
## 提交暂存区的指定文件到仓库区
git commit [file1] [file2] ... -m [message]
## 提交工作区自上次commit之后的变化，直接到仓库区
git commit -a
## 提交时显示所有diff信息
git commit -v
## 使用一次新的commit，替代上一次提交，如果代码没有任何新变化，则用来改写上一次commit的提交信息
git commit -amend -m [message]
## 重做上一次commit，并包括指定文件的新变化
git commit -amend [file1] [file2] ...




## git commit
+ git commit -m <commit message> 将暂存区的文件提交到版本库
+ git commit -am <commit message> 跳过git add 命令，直接将工作区所有已跟踪的文件提交到版本库，未跟踪的（untracked）文件不能使用该命令