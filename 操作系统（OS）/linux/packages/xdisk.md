[TOC]

# fdisk
> fdisk -l

# cfdisk
查看磁盘
> lsblk

图形化工具分区
> cfdisk /dev/nvme0n1
分两个区：root，home

格式
> EFI分区格式要求FAT32  
mkfs.fat -F 32 /dev/nvme0n1p1  
设置主分区格式EXT4  
mkfs.ext4 /dev/nvme0n1p2

# gdisk
```
> gdisk /dev/nvme0n1
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************

# boot
Command (? for help): o # create a new empty GUID partition table (GPT) 回车，y全清磁盘

Command (? for help): n # 创建分区
Partition number (1-128, default 1): #在这里按回车用它提供的默认值
First sector (34-15634398, default = 2048) or {+-}size{KMGTP}: #在这里再按回车用它提供的默认值
Last sector (2048-15634398, default = 15634398) or {+-}size{KMGTP}: +512MB
Current type is 'Apple HFS/HFS+' #无视这行

Hex code or GUID (L to show codes, Enter = AF00): EF00
Changed system type of partition to 'EFI System'

# 主目录
Command (? for help): n
Partition number (1-128, default 1): #在这里按回车用它提供的默认值
First sector (34-15634398, default = 2048) or {+-}size{KMGTP}: #在这里再按回车用它提供的默认值
Last sector (2048-15634398, default = 15634398) or {+-}size{KMGTP}: #在这里也按回车，easy
Current type is 'Apple HFS/HFS+' #无视这行
Hex code or GUID (L to show codes, Enter = AF00): 8300
Changed system type of partition to 'Linux Filesystem'

# 刷盘
Command (? for help): w
Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
The operation has completed successfully.

# 查看分区
> gdisk -l /dev/nvme0n1

# 格式化主目录
> mkfs.ext4 /dev/nvme0n1p2
```
