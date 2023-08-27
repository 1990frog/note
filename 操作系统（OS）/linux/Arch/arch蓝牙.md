[TOC]

# 安装音频与蓝牙依赖

sudo pacman -S pulseaudio-alsa bluez-utils

# 安装 libldac
mkdir -p ~/Software/AUR
cd ~/Software/AUR
git clone https://aur.archlinux.org/libldac.git
cd libldac
makepkg -si

# 安装 pulseaudio-modules-bt
标准 pulseaudio-bluetooth 包中不含 libldac 支持，从 AUR 中获取

mkdir -p ~/Software/AUR
cd ~/Software/AUR
git clone https://aur.archlinux.org/pulseaudio-modules-bt.git
cd pulseaudio-modules-bt
makepkg -si

# 查看蓝牙设备连接方式
pactl list | grep a2dp

出现 bluetooth.a2dp_codec = “LDAC” 则说明设置成功

Argument: path=/org/bluez/hci0/dev_70_26_05_CA_3F_04 autodetect_mtu=0 a2dp_config=""
Name: bluez_sink.70_26_05_CA_3F_04.a2dp_sink
Monitor Source: bluez_sink.70_26_05_CA_3F_04.a2dp_sink.monitor
        bluetooth.protocol = "a2dp_sink"
        bluetooth.a2dp_codec = "LDAC"
Name: bluez_sink.70_26_05_CA_3F_04.a2dp_sink.monitor
Monitor of Sink: bluez_sink.70_26_05_CA_3F_04.a2dp_sink
        a2dp_sink_sbc: High Fidelity Playback (A2DP Sink: SBC) (sinks: 1, sources: 0, priority: 40, available: yes)
        a2dp_sink_aac: High Fidelity Playback (A2DP Sink: AAC) (sinks: 1, sources: 0, priority: 40, available: yes)
        a2dp_sink_aptx: High Fidelity Playback (A2DP Sink: aptX) (sinks: 1, sources: 0, priority: 40, available: yes)
        a2dp_sink_aptx_hd: High Fidelity Playback (A2DP Sink: aptX HD) (sinks: 1, sources: 0, priority: 40, available: yes)
        a2dp_sink_ldac: High Fidelity Playback (A2DP Sink: LDAC) (sinks: 1, sources: 0, priority: 40, available: yes)
Active Profile: a2dp_sink_ldac
                Part of profile(s): headset_head_unit, a2dp_sink_sbc, a2dp_sink_aac, a2dp_sink_aptx, a2dp_sink_aptx_hd, a2dp_sink_ldac


# 使用 bluetoothctl 调试
重启后使用蓝牙管理器可直接配置蓝牙耳机，若出现问题，可使用 bluetoothctl 进行调试

bluetoothctl

启用蓝牙
[bluetooth]# power on
[bluetooth]# agent on
[bluetooth]# default-agent
[bluetooth]# scan on

出现类似信息则说明发现新设备
[NEW] Device 00:1D:43:6D:03:26 Lasmex LBT10

使用下列命令配对并连接
[bluetooth]# pair 00:1D:43:6D:03:26
[bluetooth]# connect 00:1D:43:6D:03:26


---

yay -S bluez bluez-utils blueman