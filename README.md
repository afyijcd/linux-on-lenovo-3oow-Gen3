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

3. make a file suspend_wifi in /usr/lib/systemd/system-sleep

sudo mkdir /usr/lib/systemd/system-sleep && cd /usr/lib/systemd/system-sleep
sudo nano suspend_wifi
[pas this:]

#!/bin/sh
if [ "${1}" == "pre" ]; then
  modprobe -rv mac80211
elif [ "${1}" == "post" ]; then
  modprobe -v mac80211
fi

sudo chmod 755 suspend_wifi
