# Quickstart guide #

In order to start logging data from your BMS123:
  * make sure SD card is inserted (there is Linux operation system)
  * plug power to MiniPC (USB 5V)
  * connect BMS123 master unit (if it is not already connected)
  * device should start logging data to SD card automatically (there is a FAT32 partition called "data" for this purpose)

Note: if you have connected USB network card you can check if the device is logging the data and also download the data on the fly. There is DHCP client so you need to find out its IP address by accessing your router. Then logs are accessible on device's IP address through your web browser (e.g. http://192.168.0.121)