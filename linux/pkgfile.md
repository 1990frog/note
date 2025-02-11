

# WIKI
[wiki](https://wiki.archlinux.org/title/Pkgfile)

# 安装
```bash
> sudo pacman -S pkgfile
> sudo pkgfile -u
```

# 使用
```bash
# 查找文件 “makepkg” 属于哪个软件包
> pkgfile makepkg
core/pacman

# 列出 archlinux-keyring包 包含的所有文件
> pkgfile -l archlinux-keyring
core/archlinux-keyring usr/
core/archlinux-keyring usr/share/
core/archlinux-keyring usr/share/pacman/
core/archlinux-keyring usr/share/pacman/keyrings/
core/archlinux-keyring usr/share/pacman/keyrings/archlinux-revoked
core/archlinux-keyring usr/share/pacman/keyrings/archlinux-trusted
core/archlinux-keyring usr/share/pacman/keyrings/archlinux.gpg
```

# 自动更新
```bash
> systemctl enable --now pkgfile-update.timer
```