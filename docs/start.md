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

TODO: Add steps and picture of running Blink sketch

### Hardware Assembly
[Link to Assembly Instructions]()

TODO: add lots of pictures

Program the Teensy with the example sketch appropriate for your display size: 16x32 or 32x32.  Make sure the board programs correctly, and look for a steady blink on the Teensy's LED.

TODO: add full steps for programming and pictures

Add the Teensy 3.1 to your assembled shield, but don't connect to the matrix display yet.  Connect your power supply to the shield and use the USB cable to connect the Teensy to your computer.

If you assembled the shield with the Self Power option, remove the power supply cable and make sure the make sure there is no blinking LED on the Teensy - it should be powered off at this point.  Now remove the USB cable and connect the power supply, and make sure there is a steady blink on the Teensy's LED.

With the external power and USB cables disconnected, connect the matrix display to the shield using the ribbon cable or plug the shield directly into the matrix display.  Make sure to connect to the INPUT connector, and not the OUTPUT connector.

If using the ribbon cable, make sure the cable is oriented correctly before powering on.

If connecting the shield directly to the display, double check the alignment of the pins.  A good way to check is to make sure the edge of the shield is flush with the edge of the shrouded connector on the display.

Power on and first look for a steady blinking on the Teensy's LED.  If there is no blink, or there is an erratic blink, remove power immediately and check the connections.

Next, look for graphics on the display.  The FeatureDemo sketch should start with a dim red background and bright white scrolling text in the center of the display.


### Troubleshooting
TODO: cleanup

Erratic blinking on Teensy without matrix connected
check soldering

Erratic blinking on Teensy after matrix connected
check connector (input vs output), orientation or cable or shield, pins inserted properly

Can't program Teensy
Self-power

Faint (red?) display with just usb and no power supply connected
- usb power is leaking into the display, disconnect usb before power, or use self-power option


### Writing your first project
Here's the bare minimum that's needed to start working with the display:

TODO: add minimum code

For a through example of all the library features, see the FeatureDemo example.

TODO: add CC license
