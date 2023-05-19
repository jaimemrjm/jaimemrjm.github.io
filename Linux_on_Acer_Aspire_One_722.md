# Linux on Acer Aspire One 722

## History

My father-in-law offered me this old mini-laptop from around 2012. I replaced the old 320 Hard Disk with Windows 7 installed with a cheap 256 GB SSD.
I bought a DDR3 4GB so-dimm module to replace the 2GB one. The two pieces from less than 20 Euros.

## (Xubuntu) Linux tips

### CPU "turbo" mode
Install the recommended requirements:

`sudo apt install build-essential git`

Compile and install the *undervolt* command:
- Download the 0.4 version from https://sourceforge.net/projects/undervolt/
- Extract, make and copy to `/usr/local/bin` for example.

AMD C-60 CPU under Linux can be "unblocked" with the [C60-tweak](https://github.com/melma/c60-tweak) tool.

```
git clone --depth=1 https://github.com/melma/c60-tweak.git
cd c60-tweak
sudo ./c60-tweak.sh 
```
The speed improvement is quite noticiable.

### GPU

The Radeon HD 6290 gpu with the `radeon` and `amdgpu` linux drivers only supports Hardware decoding for MPEG2, VC1 and H.264 (AVC) video codecs, according `vainfo` command:
```
k$ vainfo
libva info: VA-API version 1.14.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/r600_drv_video.so
libva info: Found init function __vaDriverInit_1_14
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.14 (libva 2.12.0)
vainfo: Driver version: Mesa Gallium driver 22.2.5 for AMD PALM (DRM 2.50.0 / 5.19.0-41-generic, LLVM 15.0.6)
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileNone                   :	VAEntrypointVideoProc
```

Install the package `ubuntu-restricted-extras` to get H.264 hardware acceleration. The best performance for `mpv` videoplayer I have found is with the parameters: `--vo=vdpau --hwdec=vdpau` 

## Xubuntu tips

### CPU Freq applet for XFCE Desktop

Install: `sudo apt install xfce4-cpufreq-plugin`

### Firefox

Remove firefox from snap and use the Mozilla Team PPA one.

### Blueman disable

In XFCE, go to Settings Manager > Session and Startup > [ ] Blueman (uncheck it).
Logoff and login again

## Reference

- [Puppy Linux forums](https://forum.puppylinux.com/viewtopic.php?t=236)
- [Ubuntu Wiki](https://help.ubuntu.com/community/AspireOne722)
