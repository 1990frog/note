


[archlinuxcn]
Server = http://mirrors.163.com/archlinux-cn/$arch

更新软件仓库
```
> sudo pacman -Sy
```
要想使用archlinuxcn，还需要安装密钥环
```
> sudo pacman -S archlinuxcn-keyring
```
如果密钥报错【GnuPG-2.1 与 pacman 密钥环】
由于升级到了 gnupg-2.1，pacman 上游更新了密钥环的格式，这使得本地的主密钥无法签署其它密钥。这不会出问题，除非你想自定义 pacman 密钥环。不过，我们推荐所有用户都生成一个新的密钥环以解决潜在问题。
此外，我们建议您安装 haveged，这是一个用来生成系统熵值的守护进程，它能加快加密软件（如 gnupg，包括生成新的密钥环）关键操作的速度。
要完成这些操作，请以 root 权限运行：
```
> pacman -Syu haveged
> systemctl start haveged
> systemctl enable haveged

> rm -rf /etc/pacman.d/gnupg
> pacman-key --init
> pacman-key --populate archlinux
> pacman-key --populate archlinuxcn
```