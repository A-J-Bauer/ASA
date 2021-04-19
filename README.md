# asa
Arduino Serial App, a phone ready PWA for connecting to Arduinos over the USB serial interface, providing a simple serial input and output terminal.

Installable pwa (Chrome only) here: https://a-j-bauer.github.io/asa/

You can change the baud rate to e.g. 19200 by entering:

**:baud 19200**

**Prevent reset:** When you connect to the Arduino over serial the Arduino will auto reset and your sketch will restart.
Usually this is a good thing (for uploading sketches) but sometimes you want to get some serial output from a potentially long running sketch without restarting.
In order to do that simply use a 10uF capacitor and connect it to the reset and gnd pin.


![long run nano](https://github.com/A-J-Bauer/asa/blob/main/readme_img/nanoLongRun.png)

Note: As long as the capacitor is in place you cannot upload new sketches.

The serial.js is a modified version of Google's Serial Polyfill from here https://github.com/google/web-serial-polyfill.
The modified version also works with Arduino clones on Android phones (Apple not tested).

