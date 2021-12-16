[TOC]

# 安装grub到硬盘
```
> grub-install --target = x86_64-efi --efi-directory = /boot
```

# 生成配置文件
```
> grub-mkconfig > /boot/grub/grub.cfg
```