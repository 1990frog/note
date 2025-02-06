<!-- TOC -->

- [Git的奇技淫巧:](#git%E7%9A%84%E5%A5%87%E6%8A%80%E6%B7%AB%E5%B7%A7)
    - [开卷必读](#%E5%BC%80%E5%8D%B7%E5%BF%85%E8%AF%BB)
    - [目录](#%E7%9B%AE%E5%BD%95)
    - [展示帮助信息](#%E5%B1%95%E7%A4%BA%E5%B8%AE%E5%8A%A9%E4%BF%A1%E6%81%AF)
    - [回到远程仓库的状态](#%E5%9B%9E%E5%88%B0%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93%E7%9A%84%E7%8A%B6%E6%80%81)
    - [重设第一个 commit](#%E9%87%8D%E8%AE%BE%E7%AC%AC%E4%B8%80%E4%B8%AA-commit)
    - [展示工作区和暂存区的不同](#%E5%B1%95%E7%A4%BA%E5%B7%A5%E4%BD%9C%E5%8C%BA%E5%92%8C%E6%9A%82%E5%AD%98%E5%8C%BA%E7%9A%84%E4%B8%8D%E5%90%8C)
    - [展示暂存区和最近版本的不同](#%E5%B1%95%E7%A4%BA%E6%9A%82%E5%AD%98%E5%8C%BA%E5%92%8C%E6%9C%80%E8%BF%91%E7%89%88%E6%9C%AC%E7%9A%84%E4%B8%8D%E5%90%8C)
    - [展示暂存区、工作区和最近版本的不同](#%E5%B1%95%E7%A4%BA%E6%9A%82%E5%AD%98%E5%8C%BA%E5%B7%A5%E4%BD%9C%E5%8C%BA%E5%92%8C%E6%9C%80%E8%BF%91%E7%89%88%E6%9C%AC%E7%9A%84%E4%B8%8D%E5%90%8C)
    - [快速切换到上一个分支](#%E5%BF%AB%E9%80%9F%E5%88%87%E6%8D%A2%E5%88%B0%E4%B8%8A%E4%B8%80%E4%B8%AA%E5%88%86%E6%94%AF)
    - [删除已经合并到 master 的分支](#%E5%88%A0%E9%99%A4%E5%B7%B2%E7%BB%8F%E5%90%88%E5%B9%B6%E5%88%B0-master-%E7%9A%84%E5%88%86%E6%94%AF)
    - [展示本地分支关联远程仓库的情况](#%E5%B1%95%E7%A4%BA%E6%9C%AC%E5%9C%B0%E5%88%86%E6%94%AF%E5%85%B3%E8%81%94%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93%E7%9A%84%E6%83%85%E5%86%B5)
    - [关联远程分支](#%E5%85%B3%E8%81%94%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF)
    - [列出所有远程分支](#%E5%88%97%E5%87%BA%E6%89%80%E6%9C%89%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF)
    - [列出本地和远程分支](#%E5%88%97%E5%87%BA%E6%9C%AC%E5%9C%B0%E5%92%8C%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF)
    - [查看远程分支和本地分支的对应关系](#%E6%9F%A5%E7%9C%8B%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF%E5%92%8C%E6%9C%AC%E5%9C%B0%E5%88%86%E6%94%AF%E7%9A%84%E5%AF%B9%E5%BA%94%E5%85%B3%E7%B3%BB)
    - [远程删除了分支本地也想删除](#%E8%BF%9C%E7%A8%8B%E5%88%A0%E9%99%A4%E4%BA%86%E5%88%86%E6%94%AF%E6%9C%AC%E5%9C%B0%E4%B9%9F%E6%83%B3%E5%88%A0%E9%99%A4)
    - [创建并切换到本地分支](#%E5%88%9B%E5%BB%BA%E5%B9%B6%E5%88%87%E6%8D%A2%E5%88%B0%E6%9C%AC%E5%9C%B0%E5%88%86%E6%94%AF)
    - [从远程分支中创建并切换到本地分支](#%E4%BB%8E%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF%E4%B8%AD%E5%88%9B%E5%BB%BA%E5%B9%B6%E5%88%87%E6%8D%A2%E5%88%B0%E6%9C%AC%E5%9C%B0%E5%88%86%E6%94%AF)
    - [删除本地分支](#%E5%88%A0%E9%99%A4%E6%9C%AC%E5%9C%B0%E5%88%86%E6%94%AF)
    - [删除远程分支](#%E5%88%A0%E9%99%A4%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF)
    - [重命名本地分支](#%E9%87%8D%E5%91%BD%E5%90%8D%E6%9C%AC%E5%9C%B0%E5%88%86%E6%94%AF)
    - [查看标签](#%E6%9F%A5%E7%9C%8B%E6%A0%87%E7%AD%BE)
    - [查看标签详细信息](#%E6%9F%A5%E7%9C%8B%E6%A0%87%E7%AD%BE%E8%AF%A6%E7%BB%86%E4%BF%A1%E6%81%AF)
    - [本地创建标签](#%E6%9C%AC%E5%9C%B0%E5%88%9B%E5%BB%BA%E6%A0%87%E7%AD%BE)
    - [推送标签到远程仓库](#%E6%8E%A8%E9%80%81%E6%A0%87%E7%AD%BE%E5%88%B0%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93)
    - [删除本地标签](#%E5%88%A0%E9%99%A4%E6%9C%AC%E5%9C%B0%E6%A0%87%E7%AD%BE)
    - [删除远程标签](#%E5%88%A0%E9%99%A4%E8%BF%9C%E7%A8%8B%E6%A0%87%E7%AD%BE)
    - [切回到某个标签](#%E5%88%87%E5%9B%9E%E5%88%B0%E6%9F%90%E4%B8%AA%E6%A0%87%E7%AD%BE)
    - [放弃工作区的修改](#%E6%94%BE%E5%BC%83%E5%B7%A5%E4%BD%9C%E5%8C%BA%E7%9A%84%E4%BF%AE%E6%94%B9)
    - [恢复删除的文件](#%E6%81%A2%E5%A4%8D%E5%88%A0%E9%99%A4%E7%9A%84%E6%96%87%E4%BB%B6)
    - [以新增一个 commit 的方式还原某一个 commit 的修改](#%E4%BB%A5%E6%96%B0%E5%A2%9E%E4%B8%80%E4%B8%AA-commit-%E7%9A%84%E6%96%B9%E5%BC%8F%E8%BF%98%E5%8E%9F%E6%9F%90%E4%B8%80%E4%B8%AA-commit-%E7%9A%84%E4%BF%AE%E6%94%B9)
    - [回到某个 commit 的状态，并删除后面的 commit](#%E5%9B%9E%E5%88%B0%E6%9F%90%E4%B8%AA-commit-%E7%9A%84%E7%8A%B6%E6%80%81%E5%B9%B6%E5%88%A0%E9%99%A4%E5%90%8E%E9%9D%A2%E7%9A%84-commit)
    - [修改上一个 commit 的描述](#%E4%BF%AE%E6%94%B9%E4%B8%8A%E4%B8%80%E4%B8%AA-commit-%E7%9A%84%E6%8F%8F%E8%BF%B0)
    - [查看 commit 历史](#%E6%9F%A5%E7%9C%8B-commit-%E5%8E%86%E5%8F%B2)
    - [查看某段代码是谁写的](#%E6%9F%A5%E7%9C%8B%E6%9F%90%E6%AE%B5%E4%BB%A3%E7%A0%81%E6%98%AF%E8%B0%81%E5%86%99%E7%9A%84)
    - [显示本地更新过 HEAD 的 git 命令记录](#%E6%98%BE%E7%A4%BA%E6%9C%AC%E5%9C%B0%E6%9B%B4%E6%96%B0%E8%BF%87-head-%E7%9A%84-git-%E5%91%BD%E4%BB%A4%E8%AE%B0%E5%BD%95)
    - [修改作者名](#%E4%BF%AE%E6%94%B9%E4%BD%9C%E8%80%85%E5%90%8D)
    - [修改远程仓库的 url](#%E4%BF%AE%E6%94%B9%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93%E7%9A%84-url)
    - [增加远程仓库](#%E5%A2%9E%E5%8A%A0%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93)
    - [列出所有远程仓库](#%E5%88%97%E5%87%BA%E6%89%80%E6%9C%89%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93)
    - [查看两个星期内的改动](#%E6%9F%A5%E7%9C%8B%E4%B8%A4%E4%B8%AA%E6%98%9F%E6%9C%9F%E5%86%85%E7%9A%84%E6%94%B9%E5%8A%A8)
    - [把 A 分支的某一个 commit，放到 B 分支上](#%E6%8A%8A-a-%E5%88%86%E6%94%AF%E7%9A%84%E6%9F%90%E4%B8%80%E4%B8%AA-commit%E6%94%BE%E5%88%B0-b-%E5%88%86%E6%94%AF%E4%B8%8A)
    - [给 git 命令起别名](#%E7%BB%99-git-%E5%91%BD%E4%BB%A4%E8%B5%B7%E5%88%AB%E5%90%8D)
    - [存储当前的修改，但不用提交 commit](#%E5%AD%98%E5%82%A8%E5%BD%93%E5%89%8D%E7%9A%84%E4%BF%AE%E6%94%B9%E4%BD%86%E4%B8%8D%E7%94%A8%E6%8F%90%E4%BA%A4-commit)
    - [保存当前状态，包括 untracked 的文件](#%E4%BF%9D%E5%AD%98%E5%BD%93%E5%89%8D%E7%8A%B6%E6%80%81%E5%8C%85%E6%8B%AC-untracked-%E7%9A%84%E6%96%87%E4%BB%B6)
    - [展示所有 stashes](#%E5%B1%95%E7%A4%BA%E6%89%80%E6%9C%89-stashes)
    - [回到某个 stash 的状态](#%E5%9B%9E%E5%88%B0%E6%9F%90%E4%B8%AA-stash-%E7%9A%84%E7%8A%B6%E6%80%81)
    - [回到最后一个 stash 的状态，并删除这个 stash](#%E5%9B%9E%E5%88%B0%E6%9C%80%E5%90%8E%E4%B8%80%E4%B8%AA-stash-%E7%9A%84%E7%8A%B6%E6%80%81%E5%B9%B6%E5%88%A0%E9%99%A4%E8%BF%99%E4%B8%AA-stash)
    - [删除所有的 stash](#%E5%88%A0%E9%99%A4%E6%89%80%E6%9C%89%E7%9A%84-stash)
    - [从 stash 中拿出某个文件的修改](#%E4%BB%8E-stash-%E4%B8%AD%E6%8B%BF%E5%87%BA%E6%9F%90%E4%B8%AA%E6%96%87%E4%BB%B6%E7%9A%84%E4%BF%AE%E6%94%B9)
    - [展示所有 tracked 的文件](#%E5%B1%95%E7%A4%BA%E6%89%80%E6%9C%89-tracked-%E7%9A%84%E6%96%87%E4%BB%B6)
    - [展示所有 untracked 的文件](#%E5%B1%95%E7%A4%BA%E6%89%80%E6%9C%89-untracked-%E7%9A%84%E6%96%87%E4%BB%B6)
    - [展示所有忽略的文件](#%E5%B1%95%E7%A4%BA%E6%89%80%E6%9C%89%E5%BF%BD%E7%95%A5%E7%9A%84%E6%96%87%E4%BB%B6)
    - [强制删除 untracked 的文件](#%E5%BC%BA%E5%88%B6%E5%88%A0%E9%99%A4-untracked-%E7%9A%84%E6%96%87%E4%BB%B6)
    - [强制删除 untracked 的目录](#%E5%BC%BA%E5%88%B6%E5%88%A0%E9%99%A4-untracked-%E7%9A%84%E7%9B%AE%E5%BD%95)
    - [展示简化的 commit 历史](#%E5%B1%95%E7%A4%BA%E7%AE%80%E5%8C%96%E7%9A%84-commit-%E5%8E%86%E5%8F%B2)
    - [把某一个分支到导出成一个文件](#%E6%8A%8A%E6%9F%90%E4%B8%80%E4%B8%AA%E5%88%86%E6%94%AF%E5%88%B0%E5%AF%BC%E5%87%BA%E6%88%90%E4%B8%80%E4%B8%AA%E6%96%87%E4%BB%B6)
    - [从包中导入分支](#%E4%BB%8E%E5%8C%85%E4%B8%AD%E5%AF%BC%E5%85%A5%E5%88%86%E6%94%AF)
    - [执行 rebase 之前自动 stash](#%E6%89%A7%E8%A1%8C-rebase-%E4%B9%8B%E5%89%8D%E8%87%AA%E5%8A%A8-stash)
    - [从远程仓库根据 ID，拉下某一状态，到本地分支](#%E4%BB%8E%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93%E6%A0%B9%E6%8D%AE-id%E6%8B%89%E4%B8%8B%E6%9F%90%E4%B8%80%E7%8A%B6%E6%80%81%E5%88%B0%E6%9C%AC%E5%9C%B0%E5%88%86%E6%94%AF)
    - [详细展示一行中的修改](#%E8%AF%A6%E7%BB%86%E5%B1%95%E7%A4%BA%E4%B8%80%E8%A1%8C%E4%B8%AD%E7%9A%84%E4%BF%AE%E6%94%B9)
    - [清除 gitignore 文件中记录的文件](#%E6%B8%85%E9%99%A4-gitignore-%E6%96%87%E4%BB%B6%E4%B8%AD%E8%AE%B0%E5%BD%95%E7%9A%84%E6%96%87%E4%BB%B6)
    - [展示所有 alias 和 configs](#%E5%B1%95%E7%A4%BA%E6%89%80%E6%9C%89-alias-%E5%92%8C-configs)
    - [展示忽略的文件](#%E5%B1%95%E7%A4%BA%E5%BF%BD%E7%95%A5%E7%9A%84%E6%96%87%E4%BB%B6)
    - [commit 历史中显示 Branch1 有的，但是 Branch2 没有 commit](#commit-%E5%8E%86%E5%8F%B2%E4%B8%AD%E6%98%BE%E7%A4%BA-branch1-%E6%9C%89%E7%9A%84%E4%BD%86%E6%98%AF-branch2-%E6%B2%A1%E6%9C%89-commit)
    - [在 commit log 中显示 GPG 签名](#%E5%9C%A8-commit-log-%E4%B8%AD%E6%98%BE%E7%A4%BA-gpg-%E7%AD%BE%E5%90%8D)
    - [删除全局设置](#%E5%88%A0%E9%99%A4%E5%85%A8%E5%B1%80%E8%AE%BE%E7%BD%AE)
    - [新建并切换到新分支上，同时这个分支没有任何 commit](#%E6%96%B0%E5%BB%BA%E5%B9%B6%E5%88%87%E6%8D%A2%E5%88%B0%E6%96%B0%E5%88%86%E6%94%AF%E4%B8%8A%E5%90%8C%E6%97%B6%E8%BF%99%E4%B8%AA%E5%88%86%E6%94%AF%E6%B2%A1%E6%9C%89%E4%BB%BB%E4%BD%95-commit)
    - [展示任意分支某一文件的内容](#%E5%B1%95%E7%A4%BA%E4%BB%BB%E6%84%8F%E5%88%86%E6%94%AF%E6%9F%90%E4%B8%80%E6%96%87%E4%BB%B6%E7%9A%84%E5%86%85%E5%AE%B9)
    - [clone 下来指定的单一分支](#clone-%E4%B8%8B%E6%9D%A5%E6%8C%87%E5%AE%9A%E7%9A%84%E5%8D%95%E4%B8%80%E5%88%86%E6%94%AF)
    - [clone 最新一次提交](#clone-%E6%9C%80%E6%96%B0%E4%B8%80%E6%AC%A1%E6%8F%90%E4%BA%A4)
    - [忽略某个文件的改动](#%E5%BF%BD%E7%95%A5%E6%9F%90%E4%B8%AA%E6%96%87%E4%BB%B6%E7%9A%84%E6%94%B9%E5%8A%A8)
    - [忽略文件的权限变化](#%E5%BF%BD%E7%95%A5%E6%96%87%E4%BB%B6%E7%9A%84%E6%9D%83%E9%99%90%E5%8F%98%E5%8C%96)
    - [以最后提交的顺序列出所有 Git 分支](#%E4%BB%A5%E6%9C%80%E5%90%8E%E6%8F%90%E4%BA%A4%E7%9A%84%E9%A1%BA%E5%BA%8F%E5%88%97%E5%87%BA%E6%89%80%E6%9C%89-git-%E5%88%86%E6%94%AF)
    - [在 commit log 中查找相关内容](#%E5%9C%A8-commit-log-%E4%B8%AD%E6%9F%A5%E6%89%BE%E7%9B%B8%E5%85%B3%E5%86%85%E5%AE%B9)
    - [把暂存区的指定 file 放到工作区中](#%E6%8A%8A%E6%9A%82%E5%AD%98%E5%8C%BA%E7%9A%84%E6%8C%87%E5%AE%9A-file-%E6%94%BE%E5%88%B0%E5%B7%A5%E4%BD%9C%E5%8C%BA%E4%B8%AD)
    - [强制推送](#%E5%BC%BA%E5%88%B6%E6%8E%A8%E9%80%81)
    - [git 配置 http 和 socks 代理](#git-%E9%85%8D%E7%BD%AE-http-%E5%92%8C-socks-%E4%BB%A3%E7%90%86)
    - [git 配置 ssh 代理](#git-%E9%85%8D%E7%BD%AE-ssh-%E4%BB%A3%E7%90%86)
    - [一图详解](#%E4%B8%80%E5%9B%BE%E8%AF%A6%E8%A7%A3)
    - [优雅的提交Commit信息](#%E4%BC%98%E9%9B%85%E7%9A%84%E6%8F%90%E4%BA%A4commit%E4%BF%A1%E6%81%AF)
        - [使用Commitizen代替 git commit](#%E4%BD%BF%E7%94%A8commitizen%E4%BB%A3%E6%9B%BF-git-commit)

<!-- /TOC -->

# Git的奇技淫巧:

Git是一个 “分布式版本管理工具”，简单的理解版本管理工具：大家在写东西的时候都用过 “回撤” 这个功能，但是回撤只能回撤几步，假如想要找回我三天之前的修改，光用 “回撤” 是找不回来的。而 “版本管理工具” 能记录每次的修改，只要提交到版本仓库，你就可以找到之前任何时刻的状态（文本状态）。

## 开卷必读
*如果之前未使用过 Git，可以学习 [Git 小白教程](http://rogerdudler.github.io/git-guide/index.zh.html)入门*

1. **一定要先测试命令的效果后**，再用于工作环境中，以防造成不能弥补的后果！**到时候别拿着砍刀来找我**
2. 所有的命令都在`git version 2.7.4 (Apple Git-66)`下测试通过
3. 统一概念：
	- 工作区：改动（增删文件和内容）
	- 暂存区：输入命令：`git add 改动的文件名`，此次改动就放到了 ‘暂存区’
	- 本地仓库(简称：本地)：输入命令：`git commit 此次修改的描述`，此次改动就放到了 ’本地仓库’，每个 commit，我叫它为一个 ‘版本’。
	- 远程仓库(简称：远程)：输入命令：`git push 远程仓库`，此次改动就放到了 ‘远程仓库’（GitHub 等)
	- commit-id：输出命令：`git log`，最上面那行 `commit xxxxxx`，后面的字符串就是 commit-id
4. 如果喜欢这个项目，欢迎 Star、提交 Pr、[反馈问题](https://github.com/521xueweihan/git-tips/issues)😊

## 目录
[TOC]

## 展示帮助信息
```sh
git help -g
```
The command output as below:

```
The common Git guides are:
   attributes          Defining attributes per path
   cli                 Git command-line interface and conventions
   core-tutorial       A Git core tutorial for developers
   cvs-migration       Git for CVS users
   diffcore            Tweaking diff output
   everyday            A useful minimum set of commands for Everyday Git
   glossary            A Git Glossary
   hooks               Hooks used by Git
   ignore              Specifies intentionally untracked files to ignore
   modules             Defining submodule properties
   namespaces          Git namespaces
   repository-layout    Git Repository Layout
   revisions           Specifying revisions and ranges for Git
   tutorial            A tutorial introduction to Git
   tutorial-2          A tutorial introduction to Git: part two
   workflows           An overview of recommended workflows with Git

'git help -a' and 'git help -g' list available subcommands and some concept guides. See 'git help <command>' or 'git help <concept>' to read about a specific subcommand or concept.
```

## 回到远程仓库的状态

抛弃本地所有的修改，回到远程仓库的状态。
```sh
git fetch --all && git reset --hard origin/master
```

## 重设第一个 commit

也就是把所有的改动都重新放回工作区，并**清空所有的 commit**，这样就可以重新提交第一个 commit 了

```sh
git update-ref -d HEAD
```

## 展示工作区和暂存区的不同

输出**工作区**和**暂存区**的 different (不同)。

```sh
git diff
```

还可以展示本地仓库中任意两个 commit 之间的文件变动：
```sh
git diff <commit-id> <commit-id>
```

## 展示暂存区和最近版本的不同

输出**暂存区**和本地最近的版本 (commit) 的 different (不同)。
```sh
git diff --cached
```

## 展示暂存区、工作区和最近版本的不同

输出**工作区**、**暂存区** 和本地最近的版本 (commit) 的 different (不同)。

```sh
git diff HEAD
```

## 快速切换到上一个分支

```sh
git checkout -
```

## 删除已经合并到 master 的分支

```sh
git branch --merged master | grep -v '^\*\|  master' | xargs -n 1 git branch -d
```

## 展示本地分支关联远程仓库的情况
```sh
git branch -vv
```

## 关联远程分支

关联之后，`git branch -vv` 就可以展示关联的远程分支名了，同时推送到远程仓库直接：`git push`，不需要指定远程仓库了。
```sh
git branch -u origin/mybranch
```

或者在 push 时加上 `-u` 参数
```sh
git push origin/mybranch -u
```

## 列出所有远程分支

-r 参数相当于：remote
```sh
git branch -r
```

## 列出本地和远程分支

-a 参数相当于：all
```sh
git branch -a
```

## 查看远程分支和本地分支的对应关系

```sh
git remote show origin
```

## 远程删除了分支本地也想删除

```sh
git remote prune origin
```

## 创建并切换到本地分支
```sh
git checkout -b <branch-name>
```

## 从远程分支中创建并切换到本地分支

```sh
git checkout -b <branch-name> origin/<branch-name>
```

## 删除本地分支

```sh
git branch -d <local-branchname>
```

## 删除远程分支

```sh
git push origin --delete <remote-branchname>
```

或者

```sh
git push origin :<remote-branchname>
```

## 重命名本地分支

```sh
git branch -m <new-branch-name>
```

## 查看标签

```sh
git tag
```
展示当前分支的最近的 tag

```sh
git describe --tags --abbrev=0
```

## 查看标签详细信息

```sh
git tag -ln
```

## 本地创建标签

```sh
git tag <version-number>
```

默认 tag 是打在最近的一次 commit 上，如果需要指定 commit 打 tag：
```sh
$ git tag -a <version-number> -m "v1.0 发布(描述)" <commit-id>
```

## 推送标签到远程仓库

首先要保证本地创建好了标签才可以推送标签到远程仓库：

```sh
git push origin <local-version-number>
```

一次性推送所有标签，同步到远程仓库：

```sh
git push origin --tags
```

## 删除本地标签

```sh
git tag -d <tag-name>
```

## 删除远程标签

删除远程标签需要**先删除本地标签**，再执行下面的命令：

```sh
git push origin :refs/tags/<tag-name>
```

## 切回到某个标签

一般上线之前都会打 tag，就是为了防止上线后出现问题，方便快速回退到上一版本。下面的命令是回到某一标签下的状态：
```sh
git checkout -b branch_name tag_name
```

## 放弃工作区的修改
```sh
git checkout <file-name>
```

放弃所有修改：
```sh
git checkout .
```

## 恢复删除的文件
```sh
git rev-list -n 1 HEAD -- <file_path> #得到 deleting_commit

git checkout <deleting_commit>^ -- <file_path> #回到删除文件 deleting_commit 之前的状态
```

## 以新增一个 commit 的方式还原某一个 commit 的修改

```sh
git revert <commit-id>
```

## 回到某个 commit 的状态，并删除后面的 commit

和 revert 的区别：reset 命令会抹去某个 commit id 之后的所有 commit

```sh
git reset <commit-id>  #默认就是-mixed参数。

git reset –mixed HEAD^  #回退至上个版本，它将重置HEAD到另外一个commit,并且重置暂存区以便和HEAD相匹配，但是也到此为止。工作区不会被更改。

git reset –soft HEAD~3  #回退至三个版本之前，只回退了commit的信息，暂存区和工作区与回退之前保持一致。如果还要提交，直接commit即可  

git reset –hard <commit-id>  #彻底回退到指定commit-id的状态，暂存区和工作区也会变为指定commit-id版本的内容
```

## 修改上一个 commit 的描述

如果暂存区有改动，同时也会将暂存区的改动提交到上一个 commit

```sh
git commit --amend
```

## 查看 commit 历史
```sh
git log
```

## 查看某段代码是谁写的

blame 的意思为‘责怪’，你懂的。

```sh
git blame <file-name>
```

## 显示本地更新过 HEAD 的 git 命令记录

每次更新了 HEAD 的 git 命令比如 commint、amend、cherry-pick、reset、revert 等都会被记录下来（不限分支），就像 shell 的 history 一样。
这样你可以 reset 到任何一次更新了 HEAD 的操作之后，而不仅仅是回到当前分支下的某个 commit 之后的状态。

```sh
git reflog
```

## 修改作者名

```sh
git commit --amend --author='Author Name <email@address.com>'
```

## 修改远程仓库的 url

```sh
git remote set-url origin <URL>
```

## 增加远程仓库

```sh
git remote add origin <remote-url>
```

## 列出所有远程仓库

```sh
git remote
```

## 查看两个星期内的改动
```sh
git whatchanged --since='2 weeks ago'
```

## 把 A 分支的某一个 commit，放到 B 分支上

这个过程需要 `cherry-pick` 命令，[参考](http://sg552.iteye.com/blog/1300713#bc2367928)

```sh
git checkout <branch-name> && git cherry-pick <commit-id>
```

## 给 git 命令起别名

简化命令

```sh
git config --global alias.<handle> <command>

比如：git status 改成 git st，这样可以简化命令

git config --global alias.st status
```

## 存储当前的修改，但不用提交 commit

详解可以参考[廖雪峰老师的 git 教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137602359178794d966923e5c4134bc8bf98dfb03aea3000)
```sh
git stash
```

## 保存当前状态，包括 untracked 的文件

untracked 文件：新建的文件
```sh
git stash -u
```

## 展示所有 stashes
```sh
git stash list
```

## 回到某个 stash 的状态
```sh
git stash apply <stash@{n}>
```

## 回到最后一个 stash 的状态，并删除这个 stash

```sh
git stash pop
```

## 删除所有的 stash

```sh
git stash clear
```

## 从 stash 中拿出某个文件的修改
```sh
git checkout <stash@{n}> -- <file-path>
```

## 展示所有 tracked 的文件
```sh
git ls-files -t
```

## 展示所有 untracked 的文件
```sh
git ls-files --others
```

## 展示所有忽略的文件

```sh
git ls-files --others -i --exclude-standard
```

## 强制删除 untracked 的文件

可以用来删除新建的文件。如果不指定文件文件名，则清空所有工作的 untracked 文件。`clean` 命令，**注意两点**：
1. clean 后，删除的文件无法找回
2. 不会影响 tracked 的文件的改动，只会删除 untracked 的文件

```sh
git clean <file-name> -f
```

## 强制删除 untracked 的目录

可以用来删除新建的目录，**注意**:这个命令也可以用来删除 untracked 的文件。详情见上一条

```sh
git clean <directory-name> -df
```

## 展示简化的 commit 历史
```sh
git log --pretty=oneline --graph --decorate --all
```

## 把某一个分支到导出成一个文件
```sh
git bundle create <file> <branch-name>
```

## 从包中导入分支

新建一个分支，分支内容就是上面 `git bundle create` 命令导出的内容

```sh
git clone repo.bundle <repo-dir> -b <branch-name>
```

## 执行 rebase 之前自动 stash

```sh
git rebase --autostash
```

## 从远程仓库根据 ID，拉下某一状态，到本地分支

```sh
git fetch origin pull/<id>/head:<branch-name>
```

## 详细展示一行中的修改

```sh
git diff --word-diff
```

## 清除 gitignore 文件中记录的文件

```sh
git clean -X -f
```

## 展示所有 alias 和 configs

**注意：** config 分为：当前目录（local）和全局（golbal）的 config，默认为当前目录的 config

```sh
git config --local --list (当前目录)
git config --global --list (全局)
```

## 展示忽略的文件
```sh
git status --ignored
```

## commit 历史中显示 Branch1 有的，但是 Branch2 没有 commit
```sh
git log Branch1 ^Branch2
```

## 在 commit log 中显示 GPG 签名
```sh
git log --show-signature
```

## 删除全局设置

```sh
git config --global --unset <entry-name>
```

## 新建并切换到新分支上，同时这个分支没有任何 commit

相当于保存修改，但是重写 commit 历史

```sh
git checkout --orphan <branch-name>
```

## 展示任意分支某一文件的内容

```sh
git show <branch-name>:<file-name>
```

## clone 下来指定的单一分支
```sh
git clone -b <branch-name> --single-branch https://github.com/user/repo.git
```

## clone 最新一次提交

只会 clone 最近一次提交，将减少 clone 时间

```sh
git clone --depth=1 https://github.com/user/repo.git
```

## 忽略某个文件的改动

关闭 track 指定文件的改动，也就是 Git 将不会在记录这个文件的改动

```sh
git update-index --assume-unchanged path/to/file
```

恢复 track 指定文件的改动

```sh
git update-index --no-assume-unchanged path/to/file
```

## 忽略文件的权限变化

不再将文件的权限变化视作改动

```sh
git config core.fileMode false
```

## 以最后提交的顺序列出所有 Git 分支

最新的放在最上面

```sh
git for-each-ref --sort=-committerdate --format='%(refname:short)' refs/heads/
```

## 在 commit log 中查找相关内容

通过 grep 查找，given-text：所需要查找的字段


```sh
git log --all --grep='<given-text>'
```

## 把暂存区的指定 file 放到工作区中

不添加参数，默认是 `-mixed`

```sh
git reset <file-name>
```

## 强制推送

```sh
git push -f <remote-name> <branch-name>
```

## git 配置 http 和 socks 代理

```sh
git config --global https.proxy 'http://127.0.0.1:8001'   # 适用于 privoxy 将 socks 协议转为 http 协议的 http 端口
git config --global http.proxy 'http://127.0.0.1:8001'
git config --global socks.proxy "127.0.0.1:1080"
```

## git 配置 ssh 代理

```sh
$ cat ~/.ssh/config
Host gitlab.com
ProxyCommand nc -X 5 -x 127.0.0.1:1080 %h %p    # 直接使用 shadowsocks 提供的 socks5 代理端口

Host github.com
ProxyCommand nc -X 5 -x 127.0.0.1:1080 %h %p    
```


## 一图详解

![git](https://raw.githubusercontent.com/1990frog/imagebed/default/1610692851_20191022102853197_749296005.png)

## 优雅的提交Commit信息

使用[Angular团队提交规范](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines)

主要有以下组成

* 标题行: 必填, 描述主要修改类型和内容
* 主题内容: 描述为什么修改, 做了什么样的修改, 以及开发的思路等等
* 页脚注释: 放 Breaking Changes 或 Closed Issues

常用的修改项

* type: commit 的类型
* feat: 新特性
* fix: 修改问题
* refactor: 代码重构
* docs: 文档修改
* style: 代码格式修改, 注意不是 css 修改
* test: 测试用例修改
* chore: 其他修改, 比如构建流程, 依赖管理.
* scope: commit 影响的范围, 比如: route, component, utils, build...
* subject: commit 的概述
* body: commit 具体修改内容, 可以分为多行
* footer: 一些备注, 通常是 BREAKING CHANGE 或修复的 bug 的链接.

### 使用`Commitizen`代替 git commit

可以使用[cz-cli](https://github.com/commitizen/cz-cli)工具代替 `git commit`

全局安装

```shell
npm install -g commitizen cz-conventional-changelog

echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc
```
全局安装后使用 `git cz` 代替 `git commit`就可以了,如下图

![gitcz](https://raw.githubusercontent.com/1990frog/imagebed/default/1610692851_20191022102925696_1015121465.png)

**[⬆ 返回顶部](#目录)**