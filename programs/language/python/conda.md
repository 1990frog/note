[[toc]]

# 配置变量
export PATH=/opt/anaconda/bin:$PATH

# 创建名为python36的环境。指定python版本为3.6
conda create --name python36 python=3.6

# 查看已创建的环境
conda info -e

# 激活python36环境
source activate python36