# CoreElec on X92 Android TV box

## Hardware notes

X92 is S912 based-on Soc Android TV Box. The main software issue is Amlogic has not released the GPU drivers yet.

The differences with anothers S9** models of AMLogic ([source](https://forum.kodi.tv/showthread.php?tid=255686&pid=2635832#pid2635832)):
- S905x = VP9 Profile 2 & HDR10 & 100M only Ethernet
- S905 = no VP9 Profile 2 & no HDR10 but Gigabit Ethernet
- S905D = DVB Support and VP9 + Gigabit Ethernet
- S905W = a S905 minus the Gigabit Ethernet and limited to 4K@30fps only. There is no HDR or VP9 Profile 2 hardware decoding.
- **S912** = VP9 Profile 2, HDR10, Gigabit Ethernet & Dolbyvision

## Libreelec vs Coreelec

Libreelec for Amlogic S912 devices seems to be a little bit stalled due to lack of open source GPU drivers. CoreElec project seems to pay more atention to S912 devices, so I have moved to CoreElec but the following instructions seems to be similar for both projects (Libreelec and Coreelec).

## Installation

Download the latest version from [CoreEelec github](https://github.com/CoreELEC/CoreELEC/releases/)

Create an empty zip file in the SD Card. Open the "Update" app pre-installed in Android, insert SD card with LE and choose the ZIP file in the app for update. Your box should reboot to LE. 

- Alternative method when SD Card reader doesn't work fine:
Insert a paper clip in the AV input to presh the button and power on the device (hardware reset). Release the button when the Libreelec/coreelec image appears.

DTB file required: `gxm_q200_3g.dtb`. The file `gxm_q201_3g_1gbit.dtb` should work fine but I haven't tested. Both files are included in the `device_trees` folder so it's not needed to download them, just copy it to parent folder and rename to `dtb.img`.

Further info: [Coreelec install](https://discourse.coreelec.org/t/how-to-install-coreelec/677).

## Kodi System Configuration

Please, remember to enable Video hardware acceleration for MPEG4 always. By default, it's enabled only for HD content.

## LCD Display

Frontal LCD Display works like in Android OS but it requires two steps [2](https://forum.libreelec.tv/thread/11736-led-vfd-displays-in-libreelec/):
1. Download the file `x92-vfd.conf` from (https://github.com/arthur-liberman/vfd-configurations) and copy to the path `/storage/.config/vfd.conf`.
2. Install OpenVFD addon from Coreelec official addon repo (available in the Services section).


## Remote conf

X92 modified remote with longpress buttons, thanks to boot2k3 from [libreelec forum](https://forum.libreelec.tv/thread/11643-le9-0-remote-configs-ir-keytable-amlogic-devices/?postID=81528#post81528).

## Keyboard

Check the [Kodi keyboard table](https://kodi.wiki/view/Keyboard_controls) for advanced control and monitoring when you plug a physical keyboard. Specially useful are the [codec info](https://kodi.wiki/view/Codecinfo) or *PlayerProcessInfo* (only available from Kodi 18). Check also the [shortcuts differences](https://forum.kodi.tv/showthread.php?tid=306387&pid=2520469#pid2520469) between Kodi 17 and 18.

## How to update

Leave the `.tar` file in the `/storage/.update` folder and reboot. [1](https://discourse.coreelec.org/t/how-to-update-coreelec/1037)

## Recommended repo addons

- [Thoradia](https://github.com/thoradia/thoradia): p2p network software like Transmission, qBittorrent, Jackett, Medusa, Sonarr, Radarr, etc.
