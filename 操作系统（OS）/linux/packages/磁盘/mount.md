<!-- TOC -->

- [挂载windows ntfs](#%E6%8C%82%E8%BD%BDwindows-ntfs)
- [挂载U盘](#%E6%8C%82%E8%BD%BDu%E7%9B%98)

<!-- /TOC -->

# 挂载windows ntfs
```
> sudo pacman -S ntfs-3g
> sudo mount -t ntfs-3g /dev/sda1 /mnt/hdd1
```

# 挂载U盘
```
> mount -t vfat /dev/sda1 /mnt/usb
```

