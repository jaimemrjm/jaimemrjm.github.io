# Linux on Acer Aspire One 722

## History

My father-in-law offered me this old mini-laptop from around 2012. I replaced the old 320 Hard Disk with Windows 7 installed with a cheap 256 GB SSD.
I bought a DDR3 4GB so-dimm module to replace the 2GB one. The two pieces from less than 20 Euros.

## (Xubuntu) Linux tips

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

## Xubuntu tips

### CPU Freq applet for XFCE Desktop

Install: `sudo apt install xfce4-cpufreq-plugin`

### Firefox

Remove firefox from snap and use the Mozilla Team PPA one.

### Blueman disable

In XFCE, go to Settings Manager > Session and Startup > [ ] Blueman (uncheck it).
Logoff and login again

## Reference

- https://forum.puppylinux.com/viewtopic.php?t=236
