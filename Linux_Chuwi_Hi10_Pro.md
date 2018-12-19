# Linux in the Chuwi Hi10 Pro notes

## Chuwi Hi10 Pro - first model (Intel Z8300 version)

To select boot device or enter in the EFI setup, press F7 on boot. I have the official metallic Chuwi keyboard.

[Linuxium's Ubuntu](http://linuxiumcomau.blogspot.com/) 17.04 version based on linux kernel 4.12-Release-Candidate boots fine in the Chuwi Hi10 Pro tablet by using the USB 2.0 ports in the keyboard-dock (maybe it works fine with the microUSB port). Although, I don't recommend for daily usage, see the Update below.

Devices that require to compile and install drivers (not tested yet):
- Touchscreen: [acpi driver](https://github.com/onitake/gslx680-acpi) and [firmware](https://github.com/onitake/gsl-firmware).

**Update 2017-07**
I have abandoned native Linux on this tablet because some weird issues:
- Conflicts with RemixOS (Android): when I used Linux and I booted on RemixOS after, the tablet came unstable.
- No sound output on the speakers or headphones.
- Realtker WiFi driver works bad with my home router (Orange Livebox). After some seconds, the bitrate was getting slow to ~50 kbps.
- No Video acceleration with Youtube videos on Firefox.

## Reference
2. https://techtablets.com/forum/topic/linux-mint-on-a-chuwi-hi10-tablet/
3. https://txlab.wordpress.com/2017/03/11/running-ubuntu-on-chuwi-hi10-pro-tablet/
4. https://jonathansblog.co.uk/ubuntu-on-the-chuwi-hi10-pro
5. https://github.com/danielotero/linux-on-hi10
