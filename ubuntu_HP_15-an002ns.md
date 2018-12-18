# Ubuntu on HP Pavilion 15-an002ns

## Kernel
Stop annoying kernel messages:
```
sysctl -w kernel.printk="2 4 1 7"
```
To make permanent, uncomment this line in /etc/sysctl.conf:
```
kernel.printk = 3 4 1 3
```

## NVIDIA 940m

Edit the `/etc/X11/xorg.conf` file with this content:

```
Section "Module"
    Load "modesetting"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1:0:0"
    Option "AllowEmptyInitialConfiguration"
EndSection
```
Replace PCI:1:0:0 for your nvidia Bus ID. Check the ID with:
```
lspci | grep -E "VGA|3D"
```

Install the nvidia propietary drivers from ppa:

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-367 nvidia-prime
```
And reboot the system.

If you want to use OpenCL:

```
sudo apt-get install nvidia-opencl-dev nvidia-modprobe clinfo
```

Fix Unity desktop:
Open terminal from right button on desktop, execute:
```
dconf reset -f /org/compiz/
setsid unity
```

Reference:

- http://askubuntu.com/questions/204428/unity-missing-cant-see-top-or-side-panels
- http://superuser.com/questions/351387/how-to-stop-kernel-messages-from-flooding-my-console
