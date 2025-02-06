<!-- TOC -->

- [前提](#%E5%89%8D%E6%8F%90)
- [添加box（镜像）](#%E6%B7%BB%E5%8A%A0box%E9%95%9C%E5%83%8F)
- [初始化](#%E5%88%9D%E5%A7%8B%E5%8C%96)
- [启动](#%E5%90%AF%E5%8A%A8)
- [停止](#%E5%81%9C%E6%AD%A2)
- [销毁](#%E9%94%80%E6%AF%81)
- [打开tty](#%E6%89%93%E5%BC%80tty)
- [查看状态](#%E6%9F%A5%E7%9C%8B%E7%8A%B6%E6%80%81)
- [查看ssh](#%E6%9F%A5%E7%9C%8Bssh)

<!-- /TOC -->
# 前提
virtualbox

# 添加box（镜像）
vagrant box add centos/7

# 初始化
vagrant init centos/7

# 启动
vagrant up

# 停止
vagrant halt

# 销毁
vagrant destroy

# 打开tty
vagrant ssh

# 查看状态
vagrant status

# 查看ssh
vagrant ssh-config