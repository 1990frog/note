## 蓝牙
### 安装核心包
+ bluez
+ bluez-utils
+ pulseaudio-bluetooth
+ pulseaudio-modules-bt
```
> sudo pacman -S bluez bluez-utils pulseaudio-bluetooth pulseaudio-modules-bt
> systemctl enable bluetooth
```
### win10、arch蓝牙同步
windows
1. 下载psexec(https://docs.microsoft.com/en-us/sysinternals/downloads/psexec)
2. 管理员模式运行`psexec.exe -s -i regedit`
3. 找到如下地址HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\BTHPORT\Parameters\Keys\并记录LTK（long term key）
linux
1. 切换root，进入/var/lib/bluetooth
2. 进入根目录编辑info文件，将key切换为LTK



archlinuxcn/pulseaudio-modules-bt