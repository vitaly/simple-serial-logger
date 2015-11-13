#How to prepare MiniPC

# Introduction #

This document will explain how to prepare MiniPC for simple-serial-logger application.

# Linux installation #

When you buy MiniPC (http://www.i4wifi.cz/ARM-platformy/ARM-platforma-procesor-Cortex-A9-Dual-core-1-1-1-1-6Ghz-Android-4-1-JB.html) there is Android installed.

To put Linux on it there are two basic steps:

  * prepare microSD card with Linux filesystem
  * make MiniPC boot from SD card

## Preparing SD card with filesystem ##

If you do not want to go through this process you can download already prepared filesystem from HERE. We have prepared filesystem accoring to this howto:
http://linux.autostatic.com/installing-linux-on-a-rk3066-based-device

There is also FAT partition (need to be first!) so we can read data easily from Windows based systems. This partition labeled "var" is mounted as /var. Partition labeled "linuxroot" is mounted as / and is set to read only.

### /var ###
Without having these directories in /var Apache may not start and also logging will not start.
```
/var/lock
/var/log/apache2
/var/log/logger
/var/run/apache2
```

Copy the filesystem to the SD card. You can use gparted for creating partitions.

  * create an ext partition with a label "linuxroot"
  * copy the content (/media/linuxroot is your SD Card)
```
#create SD card
tar -xvzpf homeio_rc1.tar.gz -C /media/linuxroot/

#backup SD card
cd /media/linuxroot
tar -cvzpf /sdcard_backup.tar *
```

/var partition needs to contain only a few directories.


### /etc/fstab ###
```
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/dev/root / ext4 ro,errors=remount-ro 0
/dev/disk/by-label/var /var vfat rw,auto,user,fmask=0022,dmask=0000 0 0
tmpfs    /tmp        tmpfs    defaults    0 0
tmpfs    /var/tmp    tmpfs    defaults    0 0
```


### Kernel compilation ###
  * we need USB serial adapters support

You can download kernel 3.0.36 from HERE.
We have prepared kernel according to this howto:
http://linux.autostatic.com/installing-linux-on-a-rk3066-based-device

# Linux configuration #

After you install and boot Linux you should make sure that everything works (USB LAN adapter has got IP address etc.)

### LAN connection using USB adapter ###

We have tested the device **Level One USB-0301**:
**Bus 002 Device 008: ID 0b95:772b ASIX Electronics Corp.**


File /etc/network/intefaces should be set to get adress from DHCP
```
auto lo eth0
iface eth0 inet dhcp
```
Where eth0 is your USB LAN adapter. You may need to enable the device by entering

```
ifup eth0
```