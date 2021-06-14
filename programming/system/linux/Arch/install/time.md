修改/etc/rc.conf 中的 TIMEZONE=”Asia/Shanghai”
$ sudo nano /etc/rc.conf

在/etc/localtime做个链接:
$ sudo ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

同步硬件时钟：
$ sudo hwclock  -u 或者 sudo hwclock –hctosys




方法2:
安装openNTPD，
$ sudo pacman -S openntpd

启动服务：
$ sudo /etc/rc.d/openntpd start

修改rc.conf的DAEMONS里面加上@openntpd，确保开机后台运行
$ sudo nano /etc/rc.conf

