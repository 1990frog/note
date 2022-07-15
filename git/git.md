
<!-- TOC -->

- [仓库配置](#%E4%BB%93%E5%BA%93%E9%85%8D%E7%BD%AE)
    - [配置](#%E9%85%8D%E7%BD%AE)
        - [显示当前的git配置](#%E6%98%BE%E7%A4%BA%E5%BD%93%E5%89%8D%E7%9A%84git%E9%85%8D%E7%BD%AE)
        - [编辑git配置文件[全局]](#%E7%BC%96%E8%BE%91git%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6%E5%85%A8%E5%B1%80)
        - [设置提交用户信息](#%E8%AE%BE%E7%BD%AE%E6%8F%90%E4%BA%A4%E7%94%A8%E6%88%B7%E4%BF%A1%E6%81%AF)
        - [添加远程仓库地址](#%E6%B7%BB%E5%8A%A0%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93%E5%9C%B0%E5%9D%80)
        - [修改远程仓库地址](#%E4%BF%AE%E6%94%B9%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93%E5%9C%B0%E5%9D%80)
- [查看状态](#%E6%9F%A5%E7%9C%8B%E7%8A%B6%E6%80%81)
    - [查看工作目录和暂存区的状态](#%E6%9F%A5%E7%9C%8B%E5%B7%A5%E4%BD%9C%E7%9B%AE%E5%BD%95%E5%92%8C%E6%9A%82%E5%AD%98%E5%8C%BA%E7%9A%84%E7%8A%B6%E6%80%81)
    - [查看本地代码变化状态（add操作之前）](#%E6%9F%A5%E7%9C%8B%E6%9C%AC%E5%9C%B0%E4%BB%A3%E7%A0%81%E5%8F%98%E5%8C%96%E7%8A%B6%E6%80%81add%E6%93%8D%E4%BD%9C%E4%B9%8B%E5%89%8D)
- [配置](#%E9%85%8D%E7%BD%AE)
    - [显示当前的git配置](#%E6%98%BE%E7%A4%BA%E5%BD%93%E5%89%8D%E7%9A%84git%E9%85%8D%E7%BD%AE)
    - [编辑git配置文件](#%E7%BC%96%E8%BE%91git%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)
    - [设置提交用户信息](#%E8%AE%BE%E7%BD%AE%E6%8F%90%E4%BA%A4%E7%94%A8%E6%88%B7%E4%BF%A1%E6%81%AF)
- [删除](#%E5%88%A0%E9%99%A4)
    - [删除工作区文件，并且将这次删除放入暂存区](#%E5%88%A0%E9%99%A4%E5%B7%A5%E4%BD%9C%E5%8C%BA%E6%96%87%E4%BB%B6%E5%B9%B6%E4%B8%94%E5%B0%86%E8%BF%99%E6%AC%A1%E5%88%A0%E9%99%A4%E6%94%BE%E5%85%A5%E6%9A%82%E5%AD%98%E5%8C%BA)
    - [停止追踪指定文件，单该文件会保留在工作区](#%E5%81%9C%E6%AD%A2%E8%BF%BD%E8%B8%AA%E6%8C%87%E5%AE%9A%E6%96%87%E4%BB%B6%E5%8D%95%E8%AF%A5%E6%96%87%E4%BB%B6%E4%BC%9A%E4%BF%9D%E7%95%99%E5%9C%A8%E5%B7%A5%E4%BD%9C%E5%8C%BA)
- [修改文件名](#%E4%BF%AE%E6%94%B9%E6%96%87%E4%BB%B6%E5%90%8D)

<!-- /TOC -->
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
