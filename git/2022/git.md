

# 仓库
## 创建新的 git 仓库
```
> git init
> git init <文件夹>
```
## 检出仓库
| 参数      | 操作           |
|-----------|----------------|
| -b        | 克隆指定分支   |
| --no-tags | 不克隆任何tag  |
| -o<名称>  | 自定义仓库名称 |

克隆本地仓库
```
> git clone /path/to/repository
```
克隆远端仓库
```
> git clone username@host:/path/to/repository
```

# 配置


# 工作流
你的本地仓库由 git 维护的三棵“树”组成。第一个是你的 **工作目录**，它持有实际文件；第二个是 **暂存区（Index）**，它像个缓存区域，临时保存你的改动；最后是 **仓库区（HEAD）**，它指向你最后一次提交的结果。
![](https://raw.githubusercontent.com/1990frog/imagebed/default/202207141401738.png)

## 暂存区（Index）
```
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
```
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

```
#恢复当前版本，删除工作区和缓存区的修改
> git reset --hard HEAD	

#恢复上一个版本，保留工作区，缓存区准备再次提交commit
> git reset --soft HEAD

#恢复当前版本，保留工作区，清空缓存区
> git reset --mixed HEAD

#切换到特定版本号，并删除工作区和缓存区的修改
> git reset --hard 1094a	
```

### 暂存区提交到仓库区
```
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