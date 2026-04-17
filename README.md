# linux-on-lenovo-3oow-Gen3
Installing ZorinOS (ubuntu noble numbat) on Lenovo laptop 300w Gen3 in 2026

Tried ZorinOS on this laptop and ran into several issues:
1. no touchpad after install
2. no keyboard after suspend
3. no wifi after suspend.

This is what worked for me:
1. https://askubuntu.com/questions/1557460/lenovo-300w-gen3-cant-install-ubuntu-no-trackpad

2. add i8042 to grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.direct i8042.dumbkbd"

in /etc/default/grub (sudo update-grub)

3. set powersaver=2 in network mnanager configuration

sudo nano /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

