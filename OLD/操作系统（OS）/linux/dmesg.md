sudo dmesg | grep iwlwifi


probe of 0000:04:00.0 failed with error -110


rfkill


#列出所有可用设备
rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
#关闭编号0的设备
rfkill block 0
 
#打开编号0的设备
rfkill unblock 0
 
#关闭所有wifi，蓝牙设备
rfkill block all
 
#开启所有wifi，蓝牙设备
rfkill unblock all


modprobe