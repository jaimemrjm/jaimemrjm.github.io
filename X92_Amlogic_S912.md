# CoreElec on X92 Android TV box

## Hardware notes

X92 is S912 based-on Soc Android TV Box. The main software issue is Amlogic has not released a GPU open source drivers yet. That means you need to 
stuck with the propietary blobs that need a 3.14 linux kernel.

The differences with anothers S9 family models of AMLogic ([source 1](https://forum.kodi.tv/showthread.php?tid=255686&pid=2635832#pid2635832) and [source 2](https://en.wikipedia.org/wiki/Amlogic#Media_player_SoCs_(S9_family))):
- S905x = VP9 Profile 2 & HDR10 & 100M only Ethernet
- S905 = no VP9 Profile 2 & no HDR10 but Gigabit Ethernet
- S905D = DVB Support and VP9 + Gigabit Ethernet
- S905W = a S905 minus the Gigabit Ethernet and limited to 4K@30fps only. There is no HDR or VP9 Profile 2 hardware decoding.
- **S912** = VP9 Profile 2, HDR10, Gigabit Ethernet & Dolbyvision

The new generation of S9 models of AMLogic like S905X2 and S922X add lower power comsumption, USB 3.0 and more features.

## Libreelec vs Coreelec

Coreelec is a fork from Libreelec focused on the AMLogic devices. It has the correct Linux ARM Mali GPU drivers so I have moved from Libreelec to CoreElec. The following instructions should be similar for both projects.

## Installation

- Download the latest version (image file) from [CoreElec github](https://github.com/CoreELEC/CoreELEC/releases/).

- Write the image with Libreelec installer in a USB pendrive or Micro/SD card.

- Pick the DTB file required `gxm_q201_3g_1gbit.dtb`, included in the `device_trees` folder so it's not needed to download them. Just copy it to parent folder and rename to `dtb.img`.

- Create an empty zip file in the SD Card. Open the "Update" app pre-installed in Android, insert SD card with LE and choose the ZIP file in the app for update. Your box should reboot to LE. 


> Alternative method when SD Card reader doesn't work fine:

> Insert a paper clip in the AV input to **presh and hold** the button and power on the device (hardware reset). Release the button when the CoreElec image appears and the installation starts.

Further info: [Coreelec install](https://discourse.coreelec.org/t/how-to-install-coreelec/677).

## LCD Display

Frontal LCD Display works like in Android OS but it requires two steps [2](https://forum.libreelec.tv/thread/11736-led-vfd-displays-in-libreelec/):
1. Download the file `x92-vfd.conf` from (https://github.com/arthur-liberman/vfd-configurations) and copy to the path `/storage/.config/vfd.conf`.
2. Install OpenVFD addon from Coreelec official addon repo (available in the Services section).

## Remote conf

X92 modified remote with longpress buttons, thanks to boot2k3 from [libreelec forum](https://forum.libreelec.tv/thread/11643-le9-0-remote-configs-ir-keytable-amlogic-devices/?postID=81528#post81528). [Mirror of required files](X92_remotecontrol.zip).

## Keyboard

Check the [Kodi keyboard table](https://kodi.wiki/view/Keyboard_controls) for advanced control and monitoring when you plug a physical keyboard. Specially useful are the [codec info](https://kodi.wiki/view/Codecinfo) or *PlayerProcessInfo* (only available from Kodi 18). Check also the [shortcuts differences](https://forum.kodi.tv/showthread.php?tid=306387&pid=2520469#pid2520469) between Kodi 17 and 18.

## Hardware Video Acceleration

Navigate to the Kodi menu: **Settings -> Player -> Videos -> [Render method]**:

I prefer:
- Accelerate MPEG4: [Always]
- Accelerate MPEG2: [Always]

## Enable whitelist resolution and refresh rate

Navigate to the Kode menu: **Settings -> System -> Display**:

In the [whitelist](https://kodi.wiki/view/Settings/System/Display#Whitelist), I would prefer to choose all resolutions with 60/50/23.9 Hz for TV.

Note: this whitelist menu is only available in Expert settings level.

## How to update

Leave the `.tar` file in the `/storage/.update` folder and reboot. [1](https://discourse.coreelec.org/t/how-to-update-coreelec/1037)

## How to get WLAN link speed

    iw dev wlan0 link

## Recommended repo addons

- [Thoradia](https://github.com/thoradia/thoradia): p2p network software like Transmission, qBittorrent, Jackett, Medusa, Sonarr, Radarr, etc.
- [PlexKodiConnect](https://github.com/croneter/PlexKodiConnect): Plex integration in Kodi done right

