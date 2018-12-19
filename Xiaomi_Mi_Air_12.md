# Linux distribution

I have choosed KDE Neon, but any modern Ubuntu-based distro should works fine. Manjaro and Arch Linux are reported to work fine also.

# Preparation of Live USB drive to boot the first time

Use [ROSA Image Writer](http://wiki.rosalab.ru/en/index.php/Blog:ROSA_Planet/ROSA_Image_Writer) or [Rufus](https://rufus.akeo.ie/) to assure USB drive boots in EFI mode (GPT partition squeme is required). Sometimes `dd` command doesn't work fine.

# Firmware files

DMC firmware is available in [Intel Linux Graphics Firmware](https://01.org/linuxgraphics/downloads/firmware). Installation avoids this message when update the kernel:
```
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
```

# Fixing touchpad functionality. Contribution from Maximilian S.

Modify the file `/lib/udev/hwdb.d/90-libinput-model-quirks.hwdb`, by adding the following lines to the end:
```
##########################################
# Xiaomi Air 12
##########################################

libinput:name:SYNA3105:00 06CB:7EA5:dmi:*:*
 LIBINPUT_MODEL_HP_STREAM11_TOUCHPAD=1
```
_Note_: This works because the HP Stream 11 laptop has the same issues and there is a part in the libinput source that enables exactly the feature we're looking for: Click Methods (Clickfinger to be exact).

Reboot and libinput list-devices should show an error in the first line.

# Reference

[Xiaomi Mi Notebook Air 13.3 (mostly apply to 12" model but nvidia config)](https://wiki.archlinux.org/index.php/Xiaomi_Mi_Notebook_Air_13.3)
