[TOC]

# 设置镜像
```
# 指定镜像
> npm config set registry http://registry.npm.taobao.org
# 安装镜像关联包
> npm install -g nrm
# 切换镜像
> nrm use taobao
# 查看其他镜像
> nrm ls
# 删除镜像
> nrm del 'registry_name'
# 测试镜像响应速度
> nrm test ['registry_name']
```