#How to install

## Install and configure Python ##

  * apt-get install python3-serial python-pip python-usb
  * pip install pyusb pyserial pyftdi tornado configparser

## Devices configuration ##

  * change udev rules so that logging application can easily find devices

You should create for example **/etc/udev/rules.d/99-usb-serial.rules** with following content:
```
SUBSYSTEMS=="usb",ATTRS{product}=="123\BMS",SYMLINK+="bms123"
```

This line will ensure that whenever you plug in BMS 123 master unit then it will show up as /dev/bms\_123.

## Automatic start ##

  * In order to start loggin application automatically you should add following to /etc/rc.local

```
...
```