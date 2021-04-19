# asa
Arduino Serial App, a phone ready PWA for connecting to Arduinos over the USB serial interface, providing a simple serial input and output terminal.

Installable pwa here: https://a-j-bauer.github.io/asa/

You can change the baud rate to e.g. 19200 by entering:

**:baud 19200**






When you connect to the Arduino over serial the Arduino will auto reset and your sketch will restart.
Usually this is a good thing but sometimes you want to get some serial output from a potentially long running sketch without restarting.
If you want to be ble to connect to the Arduino without restarting simply use a 10uF capacitor and connect it to the reset and gnd pins.


![long run nano](https://github.com/A-J-Bauer/asa/blob/main/readme_img/nanoLongRun.png)

Note: As long as the capacitor is in place you cannot upload new sketches.



