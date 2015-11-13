Using this app it is possible to **log data** from embedded systems via **USB serial** interface. New systems can be supported by making **new plugin** for that device. The output data is stored on internal memory (flash drive, harddrive) and can be **accessed by ethernet** or mass storage via USB. Simple-serial-logger will is being developed in python and can be **run on Linux/Windows systems**.

![http://www.i4wifi.cz/out/pictures/1/stm-rk3066.jpg](http://www.i4wifi.cz/out/pictures/1/stm-rk3066.jpg)

# Features #

  * application can run on MiniPC (RK3066 based with installed Linux)
  * periodic reading USB serial data and saving to .csv file
  * ability to download data via HTTP server
  * ability to copy data directly from the internal storage

Currently we have implemented and tested following systems:

# Plugins #

## BMS123 plugin ##

Available data:
  * current
  * total voltage
  * minimum cell value (+index)
  * maximum cell value (+index)
  * temperature max and min (+ indexes)
  * charge level
  * error state, charging bit

It is **not possible to get value of each cell**, only min/max values

### Example console output ###

2013-12-04 17:20:04 Opening serial port... press CTRL + C to close

2013-12-04 17:20:04 No device detected. Retrying in 30s.

2013-12-04 17:20:34 No device detected. Retrying in 30s.

2013-12-04 17:21:04 No device detected. Retrying in 30s.

2013-12-04 17:21:04 Connected to /dev/bms\_123

2013-12-04 17:21:52 IO error. Reconnect in 5s.

2013-12-04 17:21:57 Connected to /dev/bms\_123

2013-12-04 17:22:02 You pressed Ctrl+C!

2013-12-04 17:22:02 Waiting for threads to finish...

2013-12-04 17:22:03 Closing serial port: /dev/bms\_123

2013-12-04 17:22:03 Thread Bms123 finished.