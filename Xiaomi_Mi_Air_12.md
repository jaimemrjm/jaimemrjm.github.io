# Linux distribution

I have choosed KDE Neon, but any modern Ubuntu-based distro should works fine. Manjaro and Arch Linux are reported to work fine also.

# Preparation of Live USB drive to boot the first time

Use [ROSA Image Writer](http://wiki.rosalab.ru/en/index.php/Blog:ROSA_Planet/ROSA_Image_Writer) or [Rufus](https://rufus.akeo.ie/) to assure USB drive boots in EFI mode (GPT partition squeme is required). Sometimes `dd` command doesn't work fine.

# Firmware files

DMC firmware is available in [Intel Linux Graphics Firmware](https://01.org/linuxgraphics/downloads/firmware). Installation avoids this message when update the kernel:
```
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
```

# Touchpad

## To enable tap-to-click on Wayland

Check if the touchpad is the `event5` with the command: `sudo libinput list-devices`

Else, replace the number in the next step:
```sh
qdbus org.kde.KWin /org/kde/KWin/InputDevice/event5 org.kde.KWin.InputDevice.tapToClick true
qdbus org.kde.KWin /org/kde/KWin/InputDevice/event5 org.kde.KWin.InputDevice.pointerAccelerationProfileAdaptive true
qdbus org.kde.KWin /org/kde/KWin/InputDevice/event5 org.kde.KWin.InputDevice.pointerAcceleration 0.5
```

# Reference

- [Xiaomi Mi Notebook Air 13.3 (mostly apply to 12" model but nvidia config)](https://wiki.archlinux.org/index.php/Xiaomi_Mi_Notebook_Air_13.3)
- [reddit - Is there a way to enable tap-to-click on wayland?](https://www.reddit.com/r/kde/comments/a4i9fy/is_there_a_way_to_enable_taptoclick_on_wayland/)