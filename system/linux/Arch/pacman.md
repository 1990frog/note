[[TOC]]

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