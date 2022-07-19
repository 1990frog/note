<!-- TOC -->

- [快速检索表](#%E5%BF%AB%E9%80%9F%E6%A3%80%E7%B4%A2%E8%A1%A8)
- [Git本质](#git%E6%9C%AC%E8%B4%A8)
- [仓库](#%E4%BB%93%E5%BA%93)
    - [创建新仓库](#%E5%88%9B%E5%BB%BA%E6%96%B0%E4%BB%93%E5%BA%93)
    - [检出仓库](#%E6%A3%80%E5%87%BA%E4%BB%93%E5%BA%93)
- [配置](#%E9%85%8D%E7%BD%AE)
- [工作流](#%E5%B7%A5%E4%BD%9C%E6%B5%81)
    - [文件状态](#%E6%96%87%E4%BB%B6%E7%8A%B6%E6%80%81)
- [工作区](#%E5%B7%A5%E4%BD%9C%E5%8C%BA)
    - [工作区文件状态](#%E5%B7%A5%E4%BD%9C%E5%8C%BA%E6%96%87%E4%BB%B6%E7%8A%B6%E6%80%81)
    - [暂存区（Index）](#%E6%9A%82%E5%AD%98%E5%8C%BAindex)
    - [仓库区（Head）](#%E4%BB%93%E5%BA%93%E5%8C%BAhead)
    - [撤销操作](#%E6%92%A4%E9%94%80%E6%93%8D%E4%BD%9C)
    - [暂存区提交到仓库区](#%E6%9A%82%E5%AD%98%E5%8C%BA%E6%8F%90%E4%BA%A4%E5%88%B0%E4%BB%93%E5%BA%93%E5%8C%BA)
- [分支](#%E5%88%86%E6%94%AF)
    - [分支策略](#%E5%88%86%E6%94%AF%E7%AD%96%E7%95%A5)
        - [Merge 分支](#merge-%E5%88%86%E6%94%AF)
        - [Topic 分支](#topic-%E5%88%86%E6%94%AF)
    - [列出所有本地分支](#%E5%88%97%E5%87%BA%E6%89%80%E6%9C%89%E6%9C%AC%E5%9C%B0%E5%88%86%E6%94%AF)
    - [列出所有远程分支](#%E5%88%97%E5%87%BA%E6%89%80%E6%9C%89%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF)
    - [列出所有本地分支和远程分支](#%E5%88%97%E5%87%BA%E6%89%80%E6%9C%89%E6%9C%AC%E5%9C%B0%E5%88%86%E6%94%AF%E5%92%8C%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF)
    - [新建一个分支，但依然停留在当前分支](#%E6%96%B0%E5%BB%BA%E4%B8%80%E4%B8%AA%E5%88%86%E6%94%AF%E4%BD%86%E4%BE%9D%E7%84%B6%E5%81%9C%E7%95%99%E5%9C%A8%E5%BD%93%E5%89%8D%E5%88%86%E6%94%AF)
    - [新建一个分支，并切换到该分支](#%E6%96%B0%E5%BB%BA%E4%B8%80%E4%B8%AA%E5%88%86%E6%94%AF%E5%B9%B6%E5%88%87%E6%8D%A2%E5%88%B0%E8%AF%A5%E5%88%86%E6%94%AF)
    - [切换到指定分支，并更新工作区](#%E5%88%87%E6%8D%A2%E5%88%B0%E6%8C%87%E5%AE%9A%E5%88%86%E6%94%AF%E5%B9%B6%E6%9B%B4%E6%96%B0%E5%B7%A5%E4%BD%9C%E5%8C%BA)
    - [切换到上一个分支](#%E5%88%87%E6%8D%A2%E5%88%B0%E4%B8%8A%E4%B8%80%E4%B8%AA%E5%88%86%E6%94%AF)
    - [合并指定分支到当前分支](#%E5%90%88%E5%B9%B6%E6%8C%87%E5%AE%9A%E5%88%86%E6%94%AF%E5%88%B0%E5%BD%93%E5%89%8D%E5%88%86%E6%94%AF)
    - [删除分支](#%E5%88%A0%E9%99%A4%E5%88%86%E6%94%AF)
    - [删除远程分支](#%E5%88%A0%E9%99%A4%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF)

<!-- /TOC -->

# 快速检索表
merge   分支合并
rebase  分支衍合
cherry-pick 条件分支
squash  压合分支
checkout    检出
revert  反转提交
stash   储藏
master  主分支
Gerrit  代码审核
snapshot    快照
staging 暂存区
SHA1    哈希值
commit  提交
branch  分支
tag     标签
index   索引
origin  远程仓库

# Git本质
一套内容寻址的文件系统

# 仓库
## 创建新仓库
```sh
> git init
> git init <文件夹>
```

## 检出仓库
| 参数      | 操作           |
|-----------|----------------|
| -b        | 克隆指定分支   |
| --no-tags | 不克隆任何tag  |
| -o<名称>  | 自定义仓库名称 |

```sh
# 克隆本地仓库
> git clone /path/to/repository
# 克隆远端仓库
> git clone username@host:/path/to/repository
```

# 配置
```sh
# 显示当前的git配置
> git config --list

# 编辑git配置文件[全局]
> git config -e [--global]

# 设置全局提交用户信息
> git config [--global] user.name "[name]"
> git config [--global] user.email "[email address]"

# 设置本地提交用户信息
> git config [--local] user.name "[name]"
> git config [--local] user.email "[email address]"

# 添加远程仓库地址
> git remote add origin [远程仓库地址]
# 修改远程仓库地址
> git remote set-url origin [远程仓库地址]
```

# 工作流
你的本地仓库由 git 维护的三棵“树”组成：
+ **工作目录**，它持有实际文件
+ **暂存区（Index）**，它像个缓存区域，临时保存你的改动
+ **仓库区（HEAD）**，也叫版本库，它指向你最后一次提交的结果
  
![](https://raw.githubusercontent.com/1990frog/imagebed/default/202207141401738.png)

## 文件状态

![](https://raw.githubusercontent.com/1990frog/imagebed/default/202207191029422.png)

|中文 |    英文    |
|---|----------|
|已修改| modified |
|已暂存|  staged  |
|已提交|committed |


# 工作区
## 工作区文件状态
| 中文 |    英文    |
|----|----------|
|未被追踪|untrackec |
|被追踪 | tracked  |




## 暂存区（Index）
```sh
# 将文件的修改、文件的删除，添加到暂存区。
> git add -u

# 将文件的修改，文件的新建，添加到暂存区。
> git add .

# 将文件的修改，文件的删除，文件的新建，添加到暂存区。
> git add -A

# 会忽略.gitignore把任何文件都加入
> git add *
```

## 仓库区（Head）
```sh
# 提交暂存区到仓库区
> git commit -m [message]

# 提交暂存区的指定文件到仓库区
> git commit [file1] [file2] ... -m [message]

# 提交工作区自上次commit之后的变化，直接到仓库区
> git commit -a

# 提交时显示所有diff信息
> git commit -v

# 使用一次新的commit，替代上一次提交，如果代码没有任何新变化，则用来改写上一次commit的提交信息
> git commit --amend -m [message]

# 重做上一次commit，并包括指定文件的新变化
> git commit --amend [file1] [file2] ...
```

## 撤销操作
| 参数  | 功能                                                 | 场景                                                   |
|:------|:-----------------------------------------------------|:-------------------------------------------------------|
| hard  | 清空工作区与缓存区                                   | 放弃目标版本后所有的修改                               |
| soft  | 保留工作区与缓存区，但是把版本之间的差异存放在缓存区 | 合并多个commit                                         |
| mixed | 保留工作区清空缓存区，把版本之间的差异存放在工作区   | 1、有错误的commit需要修改；2、git reset HEAD清空缓存区 |

```sh
#恢复当前版本，删除工作区和缓存区的修改
> git reset --hard HEAD	

#恢复上一个版本，保留工作区，缓存区准备再次提交commit
> git reset --soft HEAD

#恢复当前版本，保留工作区，清空缓存区
> git reset --mixed HEAD

#切换到特定版本号，并删除工作区和缓存区的修改
> git reset --hard 1094a	
```

## 暂存区提交到仓库区
```sh
# 提交暂存区到仓库区
> git commit -m "commit"

# 提交工作区到暂存区
> git commit -a

# 提交时显示diff信息
> git commit -v
```

# 分支

## 分支策略

### Merge 分支
Merge分支是为了可以随时发布release而创建的分支，它还能作为Topic分支的源分支使用。保持分支稳定的状态是很重要的。如果要进行更改，通常先创建Topic分支，而针对该分支，可以使用Jenkins之类的CI工具进行自动化编译以及测试。
通常，大家会将master分支当作Merge分支使用。

### Topic 分支
Topic分支是为了开发新功能或修复Bug等任务而建立的分支。若要同时进行多个的任务，请创建多个的Topic分支。
Topic分支是从稳定的Merge分支创建的。完成作业后，要把Topic分支合并回Merge分支。

## 列出所有本地分支
```
> git branch
```

## 列出所有远程分支
```
> git branch -r
```

## 列出所有本地分支和远程分支
```
> git branch -a
```

## 新建一个分支，但依然停留在当前分支
```
> git branch [branch-name]
```

## 新建一个分支，并切换到该分支
```
> git checkout -b [branch]
```

## 切换到指定分支，并更新工作区
```
> git checkout [branch-name]
```

## 切换到上一个分支
```
> git checkout -
```

## 合并指定分支到当前分支
```
> git merge [branch]
```

## 删除分支
```
> git branch -d [branch-name]
```

## 删除远程分支
```
> git push origin --delete [branch-name]
> git branch -dr [remote/branch]
```