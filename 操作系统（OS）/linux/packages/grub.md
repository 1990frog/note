<!-- TOC -->

- [安装grub到硬盘](#%E5%AE%89%E8%A3%85grub%E5%88%B0%E7%A1%AC%E7%9B%98)
- [生成配置文件](#%E7%94%9F%E6%88%90%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)

<!-- /TOC -->

# 安装grub到硬盘
```
> grub-install --target = x86_64-efi --efi-directory = /boot
```

# 生成配置文件
```
> grub-mkconfig > /boot/grub/grub.cfg
```