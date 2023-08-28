[TOC]

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
