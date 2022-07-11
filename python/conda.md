<!-- TOC -->

- [配置变量](#%E9%85%8D%E7%BD%AE%E5%8F%98%E9%87%8F)
- [创建名为python36的环境。指定python版本为3.6](#%E5%88%9B%E5%BB%BA%E5%90%8D%E4%B8%BApython36%E7%9A%84%E7%8E%AF%E5%A2%83%E6%8C%87%E5%AE%9Apython%E7%89%88%E6%9C%AC%E4%B8%BA36)
- [查看已创建的环境](#%E6%9F%A5%E7%9C%8B%E5%B7%B2%E5%88%9B%E5%BB%BA%E7%9A%84%E7%8E%AF%E5%A2%83)
- [激活python36环境](#%E6%BF%80%E6%B4%BBpython36%E7%8E%AF%E5%A2%83)
- [返回默认环境](#%E8%BF%94%E5%9B%9E%E9%BB%98%E8%AE%A4%E7%8E%AF%E5%A2%83)
- [复制指定环境](#%E5%A4%8D%E5%88%B6%E6%8C%87%E5%AE%9A%E7%8E%AF%E5%A2%83)
- [删除指定环境](#%E5%88%A0%E9%99%A4%E6%8C%87%E5%AE%9A%E7%8E%AF%E5%A2%83)
- [安装包](#%E5%AE%89%E8%A3%85%E5%8C%85)
- [查看已安装的包](#%E6%9F%A5%E7%9C%8B%E5%B7%B2%E5%AE%89%E8%A3%85%E7%9A%84%E5%8C%85)
- [查看python36环境下的包](#%E6%9F%A5%E7%9C%8Bpython36%E7%8E%AF%E5%A2%83%E4%B8%8B%E7%9A%84%E5%8C%85)
- [指定环境安装包](#%E6%8C%87%E5%AE%9A%E7%8E%AF%E5%A2%83%E5%AE%89%E8%A3%85%E5%8C%85)
- [查询包信息](#%E6%9F%A5%E8%AF%A2%E5%8C%85%E4%BF%A1%E6%81%AF)
- [更新包](#%E6%9B%B4%E6%96%B0%E5%8C%85)
- [删除包](#%E5%88%A0%E9%99%A4%E5%8C%85)
- [更新conda](#%E6%9B%B4%E6%96%B0conda)
- [更新anaconda](#%E6%9B%B4%E6%96%B0anaconda)
- [更新python（大版本最新小版本）](#%E6%9B%B4%E6%96%B0python%E5%A4%A7%E7%89%88%E6%9C%AC%E6%9C%80%E6%96%B0%E5%B0%8F%E7%89%88%E6%9C%AC)
- [去除conda终端base](#%E5%8E%BB%E9%99%A4conda%E7%BB%88%E7%AB%AFbase)
- [error](#error)

<!-- /TOC -->

# 配置变量
```
export PATH=/opt/anaconda/bin:$PATH
```

# 创建名为python36的环境。指定python版本为3.6
```
conda create --name python36 python=3.6
```

# 查看已创建的环境
```
conda info -e
```

# 激活python36环境
```
source activate python36
```

# 返回默认环境
```
source deactivate python36
```

# 复制指定环境
```
conda create --name 新环境名 --clone 原环境名
```

# 删除指定环境
```
conda remove --name python36 --all
```

# 安装包
```
conda install 包
```

# 查看已安装的包
```
conda list
```

# 查看python36环境下的包
```
conda list -n python36
```

# 指定环境安装包
```
conda install -n python36 包
```

# 查询包信息
```
conda serach numpy
```

# 更新包
```
conda update -n python36 numpy
```

# 删除包
```
conda remove -n python36 numpy
```

# 更新conda
```
conda update conda
```

# 更新anaconda
```
conda update anaconda
```

# 更新python（大版本最新小版本）
```
conda update python
```

# 去除conda终端base
终端输入
```
conda deactivate
```
或者在.bash_profile或.zshrc文件中加入
```
conda deactivate
```


# error
terminals database is inaccessible
.zshrc
+ export TERMINFO=/usr/share/terminfo