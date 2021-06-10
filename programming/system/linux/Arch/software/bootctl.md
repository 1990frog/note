[TOC]

# 前置要求
fvat分区

# install
```
> bootctl install
```

# config
```
> vim /boot/loader/loader.conf
default arch
timeout 3
> vim /boot/loader/entries/arch.conf
title   Arch Linux
linux   /vmlinuz-linux
initrd  /initramfs-linux.img
> echo "options root=PARTUUID=$(blkid -s PARTUUID -o value /dev/nvme0n1p2) rw" >> /boot/loader/entries/arch.conf
```

# upload
```
> bootctl update
> systemctl enable fstrim.timer
```