<!-- TOC -->

- [pacman命令](#pacman%E5%91%BD%E4%BB%A4)
- [yay](#yay)

<!-- /TOC -->

# pacman命令
| desc                   | command                            |
| ---------------------- | ---------------------------------- |
| 安装                   | pacman -S                          |
| 删除                   | pacman -R                          |
| 移除已安装不需要软件包 | pacman -Rs                         |
| 删除一个包,所有依赖    | pacman -Rsc                        |
| 升级包                 | pacman -Syu                        |
| 查询包数据库           | pacman -Ss                         |
| 搜索以安装的包         | pacman -Qs                         |
| 显示包大量信息         | pacman -Si                         |
| 本地安装包             | pacman -Qi                         |
| 清理包缓存             | pacman -Sc                         |
| 安装本地包             | pacman -U /path/package.pkg.tar.gz |

# yay
配置  archlinuxCN 仓库
```
> sudo vim /etc/pacman.conf
//在最后添加
[archlinuxcn]
Server = https://mirrors.sjtug.sjtu.edu.cn/archlinux-cn/$arch
//顺便找到这一行，取消注释
[multilib]
Include = /etc/pacman.d/mirrorlist
```

安装
> sudo pacman -S yay

更新GPD密钥
> sudo pacman -Sy archlinuxcn-keyring

#
强烈建议开启 pacman 的颜色和多线程下载功能，编辑 /etc/pacman.conf 文件，将对应位置前 # 删除即可