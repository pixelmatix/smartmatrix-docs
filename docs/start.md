# Getting Started

### Introduction
The SmartMatrix Shield is designed to make it easy to connect the Teensy 3.1 to common RGB matrix display panels.  The SmartMatrix Library takes care of refreshing the display and provides an interface to draw to the screen, and scroll text on top of your drawing.

TODO: add picture

_
Note: Teensy 3.0 boards do work with the SmartMatrix Shield and the SmartMatrix Library, but this guide refers to Teensy 3.1 to be consistent.  A note will be added anywhere Teensy 3.0 behavior is different than Teensy 3.1.
_

There are many suppliers of RGB displays with this pinout.  The SmartMatrix Library supports driving 16x32 displays with 1/8 scan, and 32x32 displays with 1/16 scan.  Popular sources for these displays are Adafruit and Sparkfun, links below, though the only panels officially supported are included in the SmartMatrix Bundle.

TODO: add picture of pinout, and matrix displays

TODO: add links to Sparkfun and Adafruit

TODO: reference to bundle

This documentation assumes you have a general knowledge of the Teensy 3.1, how to use the Arduino IDE, and the Teensyduino addon.  If you need an overview of any of those tools, please use these references:

* [PJRC - Teensyduino](http://www.pjrc.com/teensy/teensyduino.html)
* [Arduino - Getting Started with Arduino](http://arduino.cc/en/Guide/HomePage)
* For general Teensy 3.1 support, not related to the SmartMatrix Shield or SmartMatrix Library, post a question at the [PJRC Forum](http://forum.pjrc.com/forums/3-Technical-Support-amp-Questions)

### Software and Teensy Setup
Make sure you have a supported version of the Arduino IDE and Teensyduino add-on installed.

* [Arduino IDE](http://arduino.cc/en/main/software) - only version 1.0.5
* [Teensyduino](http://www.pjrc.com/teensy/td_download.html) - only version 1.17

Use the simple blink example in the Arduino IDE to run a sketch on your Teensy 3.1.

TODO: Add steps and picture of running Blink sketch

### Hardware Assembly
[Link to Assembly Instructions]()

TODO: add lots of pictures

With an assembled board, check for normal operation of the shield without the matrix attached.  Connect your power supply to the shield and use the USB cable to connect the Teensy to your computer.  Program the Teensy with the example sketch appropriate for your display size, 16x32 or 32x32.  Make sure the board programs correctly, and look for a steady blink on the Teensy's LED.  

If you assembled the shield with the self-power option, remove the power supply cable and make sure the make sure there is no blink.  Now remove the USB cable and connect the power supply, and make sure there is a steady blink.

With the external power and USB cables disconnected, connect the matrix display to the shield using the ribbon cable or plug the shield directly into the matrix display.  Make sure to connect to the INPUT connector, and not the OUTPUT connector.

If using the ribbon cable, make sure the cable is oriented correctly before powering on.

If connecting the shield directly to the display, double check the alignment of the pins.  A good way to check is to make sure the edge of the shield is flush with the edge of the shrouded connector on the display.

Power on and first look for a steady blinking on the Teensy's LED.  Power off immediately and check the connections if there is no blink, or it is erratic.

Next, look for graphics on the display.


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
Here's the bare minimum that's needed to start working with the display

TODO: add minimum code

For a through example of all the library features, see the FeatureDemo example.
