<!-- TOC -->

- [安装](#%E5%AE%89%E8%A3%85)
- [初始化](#%E5%88%9D%E5%A7%8B%E5%8C%96)
- [引导内核](#%E5%BC%95%E5%AF%BC%E5%86%85%E6%A0%B8)
- [配置文件](#%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)

<!-- /TOC -->

# 安装
```
> sudo pacman -S refind
```

# 初始化
```
> refind-install
```

# 引导内核
```
> vim refind_linux.conf
"Boot with standard options"  "ro root=UUID=084f544a-7559-4d4b-938a-b920f59edc7e splash=silent quiet showopts "
"Boot to single-user mode"    "ro root=UUID=084f544a-7559-4d4b-938a-b920f59edc7e splash=silent quiet showopts single"
"Boot with minimal options"   "ro root=UUID=084f544a-7559-4d4b-938a-b920f59edc7e"
# This line is a comment
```

# 配置文件
/boot/EFI/refind/refind.conf
```
# 等待时间
timeout 20
# 分辨率
resolution 3840 2160
# 不扫描某磁盘
dont_scan_volumes "Recovery HD"
# 不要扫描全部的内核
scan_all_linux_kernels false
# 引入主题
include themes/rEFInd-Theme/theme.conf
```