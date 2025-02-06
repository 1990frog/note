b[TOC]

# wiki
[wiki](https://wiki.archlinuxcn.org/wiki/%E8%93%9D%E7%89%99)

# 安装
yay -S bluez bluez-utils blueman

systemctl start bluetooth

# win10、arch蓝牙同步
windows
1. 下载psexec(https://docs.microsoft.com/en-us/sysinternals/downloads/psexec)
2. 管理员模式运行`psexec.exe -s -i regedit`
3. 找到如下地址HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\BTHPORT\Parameters\Keys\并记录LTK（long term key）
linux
1. 切换root，进入/var/lib/bluetooth
2. 进入根目录编辑info文件，将key切换为LTK





hciconfig hci0 down
rmmod btusb
modprobe btusb
hciconfig hci0 up



bluetoothctl: No default controller available（没有可用的默认控件）
一些主板蓝牙控件出现错误。要查看这是否是问题所在，请运行journalctl|grep-hci。如果出现“Command tx timeout”或“Failed to read Intel version command”之类的报错，请关闭电脑电源，并拔下电源线几秒钟。这会强制控件重新加载固件（而标准重新启动不会）。请参阅此处的错误报告。

确保设备没有被rfkill阻止。

蓝牙服务无法正确识别一些英特尔卡（如8260）也可能发生这种情况。在某些情况下，使用不推荐使用的bluez utils compataAUR来代替bluez utils包据报道已经解决了这个问题。

这也可能是由电源策略[2]引起的，在这种情况下，添加内核参数btusb.enable_autosuspend=n是一个潜在的解决方案。另请参阅Red Hat Bugzilla–Bug 1573562。

有时，在没有选项的情况下重新加载btusb有助于恢复控件：

# sudo modprobe -r btusb
# sudo modprobe btusb
