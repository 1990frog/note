[TOC]

```shell
> sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack wireplumber helvum

> systemctl --user enable --now pipewire.socket
> systemctl --user enable --now pipewire-pulse.socket
> systemctl --user enable --now wireplumber.service
```