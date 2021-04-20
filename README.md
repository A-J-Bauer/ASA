# asa
Arduino Serial App, a phone ready PWA for connecting to Arduinos over the USB serial interface, providing a simple serial input and output terminal.

Installable PWA (Chrome only) here: https://a-j-bauer.github.io/asa/

For phones you need an OTG USB cable.

**Tested Arduino devices:**

* Leonardo ETH (genuine)
* MEGA 2560 R3 (genuine)
* MEGA 2560 R3 (clone)
* NANO (clone)


**Baud Rate**
You can change the baud rate to e.g. 19200 by entering ':baud 19200'.

The baud rate will be stored in local storage and therefore will persist until changed again.

![baud](https://github.com/A-J-Bauer/asa/blob/main/readme_img/baud.png)


**Prevent reset:** 

When you connect to the Arduino over serial the Arduino will auto reset and your sketch will restart.
Usually this is a good thing (for uploading sketches) but sometimes you want to get some serial output from a potentially long running sketch without restarting.
In order to do that simply use a 10uF capacitor and connect it to the reset and gnd pin.


![long run nano](https://github.com/A-J-Bauer/asa/blob/main/readme_img/nanoLongRun.png)

Note: As long as the capacitor is in place you cannot upload new sketches.

The serial.js is a modified version of Google's Serial Polyfill from here https://github.com/google/web-serial-polyfill.
The modified version helps to get the PWA to also works with Arduino clones on Android phones (Apple not tested).

A simple Arduino test sketch:

```

String msg = "";
int i=0;

void setup() {
  Serial.begin(19200);
  
  pinMode(LED_BUILTIN, OUTPUT);
  
  // blink fast to indicate startup / reset
  for (i=0; i<5; i++){
    digitalWrite(LED_BUILTIN, HIGH);
    delay(50);
    digitalWrite(LED_BUILTIN, LOW);
    delay(50);
  }

  i=0;
}

void loop() {
  digitalWrite(LED_BUILTIN, HIGH);
  delay(500);

  // check if a message was sent, if it is "reset" set the counter to 0
  if (Serial.available() > 0) {
    msg = Serial.readString();

    if (msg == "reset") {
      i=0;
    }
  }

  Serial.println(i);
  
  digitalWrite(LED_BUILTIN, LOW);
  delay(500);
   
  i++;
}
```
