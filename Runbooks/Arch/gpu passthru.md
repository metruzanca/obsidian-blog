### Grub
Add `iommu=pt` to linux cmdline (for amd)

###  vfio config
```
lspci -nn
```

```ad-info
title: My nvidia 3070ti
**gpu**: 10de:2482
**integrated audio**: 10de:228b
```

```
sudo nano /etc/modprobe.d/vfio.conf
```

Add the following

```ini
options vfio-pci ids=10de:2482,10de:228b
options vfio-pci disable_vga=1
```

