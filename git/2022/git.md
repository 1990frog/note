<!-- TOC -->

- [仓库](#%E4%BB%93%E5%BA%93)
    - [创建新的 git 仓库](#%E5%88%9B%E5%BB%BA%E6%96%B0%E7%9A%84-git-%E4%BB%93%E5%BA%93)
    - [检出仓库](#%E6%A3%80%E5%87%BA%E4%BB%93%E5%BA%93)
- [工作流](#%E5%B7%A5%E4%BD%9C%E6%B5%81)
- [分支](#%E5%88%86%E6%94%AF)
    - [分支策略](#%E5%88%86%E6%94%AF%E7%AD%96%E7%95%A5)
        - [Merge 分支](#merge-%E5%88%86%E6%94%AF)
        - [Topic 分支](#topic-%E5%88%86%E6%94%AF)
    - [切换分支](#%E5%88%87%E6%8D%A2%E5%88%86%E6%94%AF)

<!-- /TOC -->

# 仓库
## 创建新的 git 仓库
```
> git init
```
## 检出仓库
克隆本地仓库
```
> git clone /path/to/repository
```
克隆远端仓库
```
> git clone username@host:/path/to/repository
```

# 工作流
你的本地仓库由 git 维护的三棵“树”组成。第一个是你的 **工作目录**，它持有实际文件；第二个是 **暂存区（Index）**，它像个缓存区域，临时保存你的改动；最后是 **HEAD**，它指向你最后一次提交的结果。
![](https://raw.githubusercontent.com/1990frog/imagebed/default/202207141401738.png)

# 分支
## 分支策略
### Merge 分支
Merge分支是为了可以随时发布release而创建的分支，它还能作为Topic分支的源分支使用。保持分支稳定的状态是很重要的。如果要进行更改，通常先创建Topic分支，而针对该分支，可以使用Jenkins之类的CI工具进行自动化编译以及测试。
通常，大家会将master分支当作Merge分支使用。
### Topic 分支
Topic分支是为了开发新功能或修复Bug等任务而建立的分支。若要同时进行多个的任务，请创建多个的Topic分支。
Topic分支是从稳定的Merge分支创建的。完成作业后，要把Topic分支合并回Merge分支。

## 切换分支
```
> git checkout <目标分支>
```