[TOC]

# wiki
[wiki](https://wiki.archlinux.org/title/Advanced_Linux_Sound_Architecture_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#ALSA_%E5%B7%A5%E5%85%B7)

# 安装
+ alsa-utils
+ pulseaudio
+ pulseaudio-alsa

sudo pacman -S alsa-utils pulseaudio pulseaudio-alsa

pulseaudio-alsa，pulseaudio 间接解决声卡独占

# alsamixer


https://www.freesion.com/article/89381273088/


---

Master 主声卡

--

# 配置
vim .asoundrc
```
pcm.!default {
    type hw
    card 2
}

ctl.!default {
    type hw
    card 2
}
```

