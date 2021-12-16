[TOC]

# 安装
```
> sudo pacman -S refind
```

# 初始化
```
> refind-install
```

# 引导内核
引导的是linux内核，可能无法显示正确的图标，可以修改icons/os_linux.png
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