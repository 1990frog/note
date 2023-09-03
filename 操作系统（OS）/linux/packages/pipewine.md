[TOC]

Note: Helvum (GTK patchbay for PipeWire).

sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack wireplumber helvum

or

Note: qpwgraph (PipeWire Graph Qt GUI Interface).

sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack wireplumber qpwgraph
Then enable pipewire sockets and session manager:

systemctl --user enable --now pipewire.socket

systemctl --user enable --now pipewire-pulse.socket

systemctl --user enable --now wireplumber.service