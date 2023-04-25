# CoreElec on H96 MAX X4 Android TV box

## Hardware notes

H96 MAX X4 Android TV Box is based on [Amlogic S905X4 SoC](https://en.wikipedia.org/wiki/Amlogic#Media_player_SoCs_(S8_&_S9_family_gen_4)). Supports AV1 hardware decoding is working in Coreelec 20 theorically.

Ethernet is limited 100 MB and I have tested the 2GB RAM hardware version.

## Installation

[Coreelec 20.1-Nexus ne (new_era) version](https://github.com/CoreELEC/CoreELEC/releases) is working fine. Note that *ne* is preferred over *ng* because life-time support.

I have choose `sc2_s905x4_2g.dtb` device tree file for the `dtb.img`.

## LCD Display

[Pending to check]

Frontal LCD Display should work like in Android OS but it requires two steps [2](https://forum.libreelec.tv/thread/11736-led-vfd-displays-in-libreelec/):
1. Download the file `h96-max-vfd.conf` from [vfd-configurations repo](https://github.com/arthur-liberman/vfd-configurations) and copy to the path `/storage/.config/vfd.conf`.
2. Install OpenVFD addon from Coreelec official addon repo (available in the Services section).

## IR Remote config

MesonIR is working fine if you use the files from H96max x3 in the [repo](https://github.com/CoreELEC/remotes/tree/main/MesonIR/H96%20MAX%20X3) and you follow the [installation guide](https://github.com/CoreELEC/remotes/wiki/01.-Quick-installation-guide).


## Reference

- [H96 MAX X4 - Coreelec forum](https://discourse.coreelec.org/t/h96-max-x4-soc-s905x4-2g-16-1gbe-wifi-2-4ghz-bt/19372)
- [Plex addon for modern Kodi versions](https://forums.plex.tv/t/plexmod-for-kodi-18-19-20/481208)