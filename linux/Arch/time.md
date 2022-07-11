<!-- TOC -->

- [wiki](#wiki)
- [timedatectl set-timezone America/Los_Angeles](#timedatectl-set-timezone-americalos_angeles)

<!-- /TOC -->

# wiki
[wiki](https://wiki.archlinux.org/title/System_time_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

https://wiki.archlinux.org/title/System_time_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)


windows使用UTC时间

如果同时安装了 Windows 操作系统（默认使用地方时），那么一般 RTC 会被设置为地方时。Windows 其实也能处理 UTC，需要修改注册表。建议让 Windows 使用 UTC，而非让 Linux 使用地方时。Windows 使用 UTC 后，请记得禁用 Windows 的时间同步功能，以防 Windows 错误设置硬件时间。如上文所说，Linux 可以使用NTP服务来在线同步硬件时钟。

使用 regedit,新建如下 DWORD 值，并将其值设为十六进制的 1。

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation\RealTimeIsUniversal
也可以用管理员权限启动命令行来完成：

reg add "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation" /v RealTimeIsUniversal /d 1 /t REG_DWORD /f
如果以上操作不起作用，并且你使用的是 Windows 64位系统，将 DWORD 修改为 QWORD。

如果 Windows 要求根据夏令时更新时钟，可以允许。时钟仍然是 UTC，仅是显示时间会改变。

设置时间标准后需要重新设置硬件时间和系统时间。 updated。

如果你有时间偏移问题，重新安装 tzdata 并再次设置你的时区:

# timedatectl set-timezone America/Los_Angeles
