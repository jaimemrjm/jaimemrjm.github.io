# Linux on my Acer Aspire A514-54G laptop

# Hardware

- Proccessor: Intel® Core™ i5-1135G7 Quad-core 2.40 GHz
- Screen: 35,6 cm (14") Full HD (1920 x 1080) 16:9 IPS
- Memory: 8 GB (4 GB soldered on-board + 4 GB in slot) DDR4 SDRAM
- Disk: 512 GB M.2 NVMe
- GPU: Intel® Iris Xe Graphics G7 80 EUs "Gen12"
- WiFi: Intel Wi-Fi 6 AX201
- Power Adapter: Delta ADP-45FE F (19V, 2.37A, 45W), plug 3.0x1.0mm

# UEFI / BIOS notes

F2 key to enter in BIOS menu
F12 key (after enable in BIOS) to choose boot menu
Ctrl+S combination keys to enable extra BIOS options in Main menu like "VMD mode" or "Touchpad mode".

# Windows notes

Notes to disable VMD / Intel Octane Storage management (a.k.a RST mode for SATA) to prepare Linux installation.

## How to enable safeboot in the Acer OEM Windows

Open Administrator prompt:
`bcdedit /set safeboot minimal`

## How to disable safeboot

If keyboard or left mouse button doesn't work fine, restart from advanced Startup Options, enter in the Troubleshoot -> Advanced Options and then start in Safemode with command line options. Then execute:
`bcdedit /deletevalue safeboot` 

# Linux

## Intel Iris Xe GPU

Note that the GPU is *Gen12* even the CPU is Intel 11th Gen (Tiger Lake). It supports GuC and HuC. The best video player to get hardware video acceleration in my test has been Totem from Gnome. I recommend the command `intel_gpu_top` to verify everything is fine.

- Firefox tip: Enable "media.ffmpeg.vaapi.enabled" in `about:config` to get VA-API acceleration.

- Enable the GUC, HUC and Framebuffer compression features

Edit the file `/etc/modprobe.d/i915.conf` with the content:
```
options i915 enable_guc=3
options i915 enable_fbc=1
```
and update your intramfs. Depending your linux distribution ([Fedora](https://discussion.fedoraproject.org/t/intel-graphics-best-practices-and-settings-for-hardware-acceleration/69944#h-4-enable-intel-guc-and-huc-and-framebuffer-compression-5) example, [Ubuntu](https://askubuntu.com/a/897330/24536) example).

Whatever linux distro you use, is interesting to check the [Arch Linux wiki](https://wiki.archlinux.org/title/Intel_graphics#Enable_GuC_/_HuC_firmware_loading).

## Intel HDA Soundcard - Realtek ALC255 Codec

Intenal microphone just works but external microphone (headphone mini-jack) doesn't work for me. I have tried this config:
```
❯ cat /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=alc255-acer
```
[Fedora bug open](https://bugzilla.redhat.com/show_bug.cgi?id=2208877)

# References
1. [Laptopmedia - Hardware review](https://laptopmedia.com/es/review/acer-aspire-5-a514-54-review-budget-tiger-lake-laptops-are-coming/)
2. [Community Acer - Intalling Linux on A515-55](https://community.acer.com/en/discussion/607762/installing-linux-on-my-new-aspire-5-a515-55)
3. [Debian Wiki - InstallingDebianOnAcerAspire 5 A515-56](https://wiki.debian.org/InstallingDebianOn/Acer/Aspire%205%20A515-56)
4. [How to disable safe mode in Windows 11](https://technoresult.com/how-to-disable-safe-mode-in-windows-11/)
5. [Intel Graphics - Best practices and settings for hardware acceleration?](https://discussion.fedoraproject.org/t/intel-graphics-best-practices-and-settings-for-hardware-acceleration/69944)
6. [Arch wiki - Hardware video acceleration - Verification](https://wiki.archlinux.org/title/Hardware_video_acceleration#Verification)
7. [skylake-tuning-linux.md gist](https://gist.github.com/Brainiarc7/aa43570f512906e882ad6cdd835efe57)
8. [Restore Windows after Linux install](https://community.acer.com/en/discussion/comment/1033795/#Comment_1033795)
