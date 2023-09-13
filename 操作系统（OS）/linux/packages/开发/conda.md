[TOC]

# 安装
yay -S miniconda

# 配置变量
```
export PATH=/opt/anaconda/bin:$PATH
```

# 初始化
```
> conda init <SHELL_NAME>
Currently supported shells are:
  - bash
  - fish
  - tcsh
  - xonsh
  - zsh
  - powershell
```

---


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