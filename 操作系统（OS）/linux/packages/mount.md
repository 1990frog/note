<!-- TOC -->

- [挂载windows ntfs](#挂载windows-ntfs)
- [挂载U盘](#挂载u盘)

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