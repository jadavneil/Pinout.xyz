<!--
---
name: 1 Wire Pi Plus
class: board
type: com
formfactor: HAT
image: 'ab-1-wire-pi-plus.png'
manufacturer: AB Electronics
description: 1-Wire to I2C host interface
url: https://www.abelectronics.co.uk/p/60/1-Wire-Pi-Plus
github: https://github.com/abelectronicsuk
buy: https://www.abelectronics.co.uk/p/60/1-Wire-Pi-Plus
pincount: 40
eeprom: no
power: 3v3,5v
pin:
  '3':
    mode: i2c
  '5':
    mode: i2c
i2c:
  '0x18':
    name: DS2482
    device: DS2482-100
-->
#1 Wire Pi Plus

The 1 Wire Pi Plus from AB Electronics UK is a communication board supporting the 1-Wire® protocol designed for use on the Raspberry Pi A+, Raspberry Pi B+ and Raspberry Pi 2 Model B computer platforms.  A 5V buffered I2C port is also provided on the board. 

The 1-Wire® port on the 1 Wire Pi Plus is based around a DS2482-100 I2C to 1-Wire® bridge device.  The DS2482-100 provides bi-directional protocol conversion between the I2C port on the Raspberry Pi and any attached 1-Wire® slave devices.  An ESD Protection Diode is used to protect the 1 Wire Pi Plus and Raspberry Pi from electrostatic spikes on the 1-Wire® port.  Connections to the 1-Wire® port can be made through the RJ-12 socket or the solder points on the PCB.

The Quick2wire lib from [https://github.com/quick2wire/quick2wire-python-api](https://github.com/quick2wire/quick2wire-python-api) allows easy access to the I2C port via Python.

[https://www.abelectronics.co.uk/kb/article/3/owfs-with-i2c-support-on-raspberry-pi](https://www.abelectronics.co.uk/kb/article/3/owfs-with-i2c-support-on-raspberry-pi "Configuring and using the 1-Wire® port on your Raspberry Pi")