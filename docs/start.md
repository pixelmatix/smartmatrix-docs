# Getting Started

### Introduction
The SmartMatrix Shield is designed to make it easy to connect the Teensy 3.1 to common types of RGB LED matrix display panels.  The SmartMatrix Library takes care of refreshing the LED driver circuitry on the display and provides an interface to draw to a virtual screen, and scroll text on top of the drawing.
> ![SmartMatrix Shield](photos/ProtoIsometric.JPG)

> ![Display Variations (Front)](photos/DisplayVariationsFront.JPG)
> ![Display Variations (Back)](photos/DisplayVariationsBack.JPG)

There are many suppliers of RGB displays with this pinout.  The SmartMatrix Library supports driving 16x32 displays with 1/8 scan, and 32x32 displays with 1/16 scan.  Popular sources for these displays in the Maker Community are Adafruit and Sparkfun, links below.  
<br/>
[Adafruit Medium 16x32 Panel](http://www.adafruit.com/products/420)  
[Adafruit Medium 32x32 Panel](http://www.adafruit.com/products/1484)  
[Sparkfun 16x32 Panel](https://www.sparkfun.com/products/12583)  
[Sparkfun 32x32 Panel](https://www.sparkfun.com/products/12584)  
<br/>
The SmartMatrix Library and SmartMatrix Shield has been tested with an Adafruit 16x32 Display purchased in November 2013.  The Library and Shield _should_ work with the Adafruit Medium 32x32 display and the displays from Sparkfun, but it will probably not work with the Adafruit Small 32x32 display which has two input connectors.

> ![Display Pinout](photos/DisplayPinout.JPG)

This documentation assumes you have a general knowledge of the Teensy 3.1, how to use the Arduino IDE, and the Teensyduino addon.  If you need an overview of any of those tools, please use these references:

* [PJRC - Teensyduino](http://www.pjrc.com/teensy/teensyduino.html)
* [Arduino - Getting Started with Arduino](http://arduino.cc/en/Guide/HomePage)
* For general Teensy 3.1 support, not related to the SmartMatrix Shield or SmartMatrix Library, post a question at the [PJRC Forum](http://forum.pjrc.com/forums/3-Technical-Support-amp-Questions)

_Note for Teensy 3.0 users: Teensy 3.0 boards do work with the SmartMatrix Shield and the SmartMatrix Library, but this guide refers to Teensy 3.1 to be consistent.  A note will be added anywhere Teensy 3.0 behavior is different than Teensy 3.1._

### Software and Teensy Setup
Make sure you have a supported version of the Arduino IDE and Teensyduino add-on installed.

* [Arduino IDE](http://arduino.cc/en/main/software) - only version 1.0.5
* [Teensyduino](http://www.pjrc.com/teensy/td_download.html) - only version 1.17

Before continuing, use the blink example in the Arduino IDE to verify you can compile and run a sketch on your Teensy 3.1.
