# SmartMatrix Overview

### Introduction
The SmartMatrix Library is an Arduino library written specifically for the Teensy 3.1 microcontroller development system.  Using the powerful DMA hardware built into the Teensy 3's microcontroller, the library takes care of refreshing the LED driver circuitry on the display with 24-bits of color depth, and provides an interface to draw to a virtual screen and scroll text on top of the drawing.


### Large RGB LED Matrix Display Panels
The supported RGB matrix display panels are designed to be used in large scale video advertising screens, and come in different sizes and pixel pitches, with driver circuitry built into the board.  The panels require an external controller to refresh the display.

> ![Display Variations (Front)](photos/DisplayVariationsFront.jpg)  
> 6mm pitch 16x32, 5mm pitch 32x32, 6mm pitch 32x32

There doesn't seem to be an official standard for these displays, but they usually have the same 2x8 connector and pinout for connecting to a controller board.  Power is supplied to the displays through a separate connection: either two screw terminals, or a 4-pin 0.156" spacing connector.

> ![Display Variations (Back)](photos/DisplayVariationsBack.jpg)
> ![Display Pinout](photos/DisplayPinout.jpg)

There are many suppliers of RGB displays with this pinout.  The SmartMatrix Library supports driving 16x32 displays with 1/8 scan, and 32x32 displays with 1/16 scan.  Popular sources for these displays in the Maker Community are Adafruit and Sparkfun, links below.  
<br/>
[Adafruit Medium 16x32 Panel](http://www.adafruit.com/products/420)  
[Adafruit Medium 32x32 Panel](http://www.adafruit.com/products/1484)  
[Sparkfun 16x32 Panel](https://www.sparkfun.com/products/12583)  
[Sparkfun 32x32 Panel](https://www.sparkfun.com/products/12584)  
<br/>
The SmartMatrix Library and SmartMatrix Shield has been tested with an Adafruit 16x32 Display purchased in November 2013.  The Library and Shield _should_ work with the Adafruit Medium 32x32 display and the displays from Sparkfun, but it will likely not work with the Adafruit Small 32x32 display which has two input connectors.

The displays are also available directly from suppliers in China using [Aliexpress.com](http://www.aliexpress.com/).  Search for "P5" or "P6" referring to the 5mm or 6mm pitch between LEDs and "Indoor RGB" to pull up a lot of results.  The prices may be a bit cheaper, but you will not get the same customer service as you would from Adafruit or Sparkfun.

### Connecting Teensy and Display
The SmartMatrix Shield is the best way to connect the Teensy 3.1 to compatible Large RGB LED matrix display panels.  The shield makes it easy to connect the 13 signals required to drive the display, connects an external power supply to the display and Teensy, and brings out the Teensy's free signals to a convenient header.
> ![SmartMatrix Shield](photos/ProtoIsometric.jpg)

The SmartMatrix Shield includes multiple options for connecting the Shield to the display, using either the ribbon cable included with the display, or attaching the shield directly to the display.  The shield included two connectors for power, to match the two main types of power cables included with these displays.

See more details on the shield here:  
[SmartMatrix Shield](shieldref.html)

A Teensy 3.1 can also be connected to the display panel using individual wires.  Follow the wiring for the 13 signals between J1 and U1 in the [SmartMatrix Shield schematic](https://github.com/pixelmatix/SmartMatrix/raw/master/hardware/SmartMatrixShield_V1_sch.pdf), as well as ground.  Make sure to connect the LATCH signal to both pins on the Teensy, as well as the display connector.
> ![Manual Wiring](photos/TeensyManualWiring.jpg)


### Software and Teensy Setup
This documentation assumes you have a general knowledge of the Teensy 3.1, how to use the Arduino IDE, and the Teensyduino addon.  If you need an overview of any of those tools, please use these references:

* [PJRC - Teensyduino](http://www.pjrc.com/teensy/teensyduino.html)
* [Arduino - Getting Started with Arduino](http://arduino.cc/en/Guide/HomePage)
* For general Teensy 3.1 support, not related to the SmartMatrix Shield or SmartMatrix Library, post a question at the [PJRC Forum](http://forum.pjrc.com/forums/3-Technical-Support-amp-Questions)

_Note for Teensy 3.0 users: Teensy 3.0 boards do work with the SmartMatrix Shield and the SmartMatrix Library, but this guide refers to Teensy 3.1 to be consistent.  A note will be added anywhere Teensy 3.0 behavior is different than Teensy 3.1._

Make sure you have a supported version of the Arduino IDE and Teensyduino add-on installed.

* [Arduino IDE](http://arduino.cc/en/main/software) - only version 1.0.5
* [Teensyduino](http://www.pjrc.com/teensy/td_download.html) - only version 1.18

Before continuing, use the blink example in the Arduino IDE to verify you can compile and run a sketch on your Teensy 3.1.

TODO: add instructions on installation of library, and running example sketch
