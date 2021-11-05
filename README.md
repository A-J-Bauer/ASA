# asa
Arduino Serial App, 
a phone ready PWA for connecting to Arduinos over the USB serial interface, providing a simple serial input and output terminal. Installable PWA (Chrome only) here: https://a-j-bauer.github.io/asa/

![screenshot](https://github.com/A-J-Bauer/asa/blob/main/docimg/screenshot.png)

**Tested Arduino devices:**
* Uno (genuine)
* Leonardo ETH (genuine)
* MEGA 2560 R3 (genuine)
* MEGA 2560 R3 (clone)
* NANO (clone)

**Other devices:**
* Raspberry Pi Zero 2 W

  RPi setup: Add 'dtoverlay=dwc2' to /boot/config.txt, insert 'modules-load=dwc2,g_serial' into /boot/cmdline.txt after 'rootwait', reboot. Test with 'echo "test" > /dev/ttyGS0'

For phones you need an OTG USB cable.

**Source Note:**
The serial.js is a modified version of Google's Serial Polyfill from here https://github.com/google/web-serial-polyfill.
The modified version helps to get the PWA to also works with Arduino clones on Android phones (Apple not tested).
