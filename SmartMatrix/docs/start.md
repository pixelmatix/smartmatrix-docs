# SmartMatrix Overview

### Introduction
The SmartMatrix Shield is the best way to connect the Teensy 3.1 to compatible Large RGB LED matrix display panels, and in combination with the SmartMatrix Library can create stunning LED visuals with just a few lines of code.  You can also use the prebuilt [Aurora software](https://github.com/pixelmatix/aurora) that creates an interactive display to play animated GIFs and patterns using the SmartMatrix Shield, for those who want to easily get started or don't want to write their own code.

> ![Aurora Demo](photos/AuroraDemo.jpg)
> Example display created using the SmartMatrix SD Shield, 32x32 P6 LED Matrix Panel, and SmartMatrix Frame Kit installed in a shadowbox picture frame.  
> [Click for Video](https://www.youtube.com/watch?v=alcExtbLE3w&feature=youtu.be)

The SmartMatrix Shield is available for purchase from [Adafruit](https://www.adafruit.com/products/1902).  Compatible RGB matrix panels are available from Adafruit and linked from their SmartMatrix Shield product page.  The SmartMatrix Bundle - which comes with everything you need to build a display that can be mounted in a shadowbox picture frame and comes with a remote control to change what's playing - is available through the [Hackaday Store](http://store.hackaday.com/products/smartmatrix-bundle) with free worldwide shipping.

> ![SmartMatrix Shield](photos/ProtoIsometric.jpg)

All of our products are sold as kits and require some soldering.  If you are interested in purchasing a complete product and not a kit, [sign up for our email list](http://eepurl.com/UX2V5) to get notified when this is available.

For an overview of the types of projects you can do with the SmartMatrix Shield, see [our guides on the Adafruit Learning System](https://learn.adafruit.com/users/Pixelmatix).

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
[Adafruit 32x32 Panel - 6mm Pitch](http://www.adafruit.com/products/1484)  
[Adafruit 32x32 Panel - 5mm Pitch](http://www.adafruit.com/products/2026)  
[Adafruit 32x32 Panel - 4mm Pitch](http://www.adafruit.com/products/607)  
[Sparkfun 16x32 Panel](https://www.sparkfun.com/products/12583)  
[Sparkfun 32x32 Panel](https://www.sparkfun.com/products/12584)  
<br/>
The SmartMatrix Library and SmartMatrix Shield has been tested with an Adafruit 16x32 Display purchased in November 2013, and Adafruit's 4mm, 5mm and 6mm pitch displays purchased in November 2014.  The Library and Shield should work the displays from Sparkfun, but they have not been tested.

The displays are also available directly from suppliers in China using [Aliexpress.com](http://www.aliexpress.com/).  Search for "P5" or "P6" referring to the 5mm or 6mm pitch between LEDs and "Indoor RGB" to pull up a lot of results.  The prices may be a bit cheaper, but you will not get the same customer service as you would from Adafruit or Sparkfun, and you may get a [defective display](https://plus.google.com/113700969348903612932/posts/dmweg9newJa), or a [display that is incompatible](https://muut.com/pixelmatix#!/support:mirrored-text-start-coord) with the SmartMatrix Library, without a good way to return them.

Currently the SmartMatrix Library has support for 32x32 and 16x32 panels, though most of the included examples and projects based on the library are optimized for 32x32 panels and some functionality is not available for 16x32 panels.  These panels are designed to be chained together, though the SmartMatrix Library does not have support for drawing to more than one panel right now.  Some users have made their own forks of the library to support multiple panels: [here](https://github.com/pixelmatix/SmartMatrix/pull/2), [here](https://github.com/pixelmatix/SmartMatrix/pull/7), and [here](https://github.com/pixelmatix/SmartMatrix/pull/17).

### Connecting Teensy and Display
The SmartMatrix Shield is the best way to connect the Teensy 3.1 to compatible Large RGB LED matrix display panels.  The shield makes it easy to connect the 13 signals required to drive the display, connects an external 5V supply to power the display and Teensy, and brings out the Teensy's free signals to a convenient header.
> ![SmartMatrix Shield](photos/ProtoIsometric.jpg)

The SmartMatrix Shield includes multiple options for connecting the Shield to the display, using either the ribbon cable included with the display, or attaching the shield directly to the display.  The shield includes two connectors for power, matching the two main types of power cables included with these displays.

See more details on the shield and assembly instructions here:  
[SmartMatrix Shield](shieldref.html)

The Shield is available for purchase from [Adafruit](https://www.adafruit.com/products/1902) and [PJRC](http://www.pjrc.com/store/smartmatrix_kit.html), as well as some other distributors listed on [the Shop page](shop.html).

A Teensy 3.1 can also be connected to the display panel using individual wires.  Follow the wiring for the 13 signals between J1 and U1 in the [SmartMatrix Shield schematic](https://github.com/pixelmatix/SmartMatrix/raw/master/hardware/SmartMatrixShield_V1_sch.pdf), as well as ground.  Make sure to connect the LATCH signal to both pins on the Teensy, as well as the display connector.
> ![Manual Wiring](photos/TeensyManualWiring.jpg)


### Power

Connect power to the board through the 5.5mm OD, 2.1mm ID positive tip barrel jack connector.  This connector is a common size in power supplies and Adafruit seems to have standardized on it.

The display draws up to 3.5A at 5V when displaying full white.  A 5V 4A DC adapter is recommended for powering the display and Teensy.  Adafruit sells one [here](http://www.adafruit.com/products/1466).  Sparkfun did not carry a suitable power supply when I checked.

For some reason both Adafruit and Sparkfun say these panels draw only 2A max, which isn't correct.  Here's an article that shows some power supply current measurements for these panels:  
[Octoscroller - NYC Resistor](http://www.nycresistor.com/2013/09/12/octoscroller/)

Both the 16x32 and 32x32 panels will have similar current draw, which may seem strange at first examination, but both panels only light up two rows at a time when refreshing (one in the top half and one in the bottom half).  At any moment in time, either display will only have up to 64 LEDs lit at once.  The 16x32 panel scans through eight row pairs per frame, and the 32x32 panels scans through 16 row pairs per frame.  The 32x32 panel refreshes twice the number of rows, but spends half the amount of time driving each row.


### Software and Teensy Setup
This documentation assumes you have a general knowledge of the Teensy 3.1, how to use the Arduino IDE, and the Teensyduino addon.  If you need an overview of any of those tools, please use these references:

* [PJRC - Teensyduino](http://www.pjrc.com/teensy/teensyduino.html)
* [Arduino - Getting Started with Arduino](http://arduino.cc/en/Guide/HomePage)
* For general Teensy 3.1 support, not related to the SmartMatrix Shield or SmartMatrix Library, post a question at the [PJRC Forum](http://forum.pjrc.com/forums/3-Technical-Support-amp-Questions)

_Note for Teensy 3.0 users: Teensy 3.0 boards do work with the SmartMatrix Shield and the SmartMatrix Library, but this guide refers to Teensy 3.1 to be consistent.  A note will be added anywhere Teensy 3.0 behavior is different than Teensy 3.1._

Make sure you have a supported version of the Arduino IDE and Teensyduino add-on installed.

* [Arduino IDE](http://arduino.cc/en/main/software) - version 1.0.5 or 1.0.6
* [Teensyduino](http://www.pjrc.com/teensy/td_download.html) - only version 1.20

Before continuing, use the blink example in the Arduino IDE to verify you can compile and run a sketch on your Teensy 3.1.

Download the latest version of the SmartMatrix Library:  
[SmartMatrix Releases - GitHub](https://github.com/pixelmatix/SmartMatrix/releases)

Import either the "16x32" or "32x32" library depending on what resolution display you have.  If you want to work with both resolutions, import both.  See instructions from Arduino here:  
[Arduino - Libraries](http://arduino.cc/en/Guide/Libraries)

Start with the FeatureDemo Example project, included with the library.  From the Arduino File menu, choose Examples, the appropriate SmartMatrix library for your display resolution, then FeatureDemo.  

You should already have most of the correct settings to load the FeatureDemo sketch on your Teensy, from running the blink example earlier.  Under Tools, CPU Speed, make sure either 48 MHz or 96MHz (overclock) is selected.

Click the Upload button, and the sketch should compile and upload to your Teensy, and start running right away.

You can use the FeatureDemo sketch as a way to get started with your own project.  Inside loop(), find a demo section that is similar to what you want to do with your project, delete the other sections, and save it as as new sketch.

### External Libraries

Some SmartMatrix examples require external libraries to compile.  You may already have older versions of these libraries installed in Arduino that may be too old to work with SmartMatrix and the examples.

Installing Arduino libraries from GitHub has a couple pitfalls.  [This Adafruit tutorial](https://learn.adafruit.com/adafruit-all-about-arduino-libraries-install-use/) explains the basics of installing libraries and how to avoid the pitfalls.

**FastLED**  
If you're having trouble compiling Aurora and are getting errors that refer to FastLED.h, try compiling one of the simpler FastLED examples first, which will help narrow down the issue.  
`FastLED_Controller`  
`FastLED_Functions`

This error means the FastLED library isn't installed (correctly):  
`fatal error: FastLED.h: No such file or directory`

The latest version of Teensyduino includes FastLED version 2.0 which is too old to work with SmartMatrix.  We need version 3.0 or later which is [available from GitHub](https://github.com/FastLED/FastLED/releases) and not included with Teensyduino.  If you see any of these errors, you likely have an older version of FastLED installed:  
`no known conversion for argument 4 from 'CRGB' to 'const rgb24&'`  
`error: 'inoise8' was not declared in this scope`

This can be tricky to track down as Teensyduino installs libraries into your Arduino application directory, which might not be in your Arduino sketchbook.  For OSX you will need to navigate into the the Arduino.app package to find the libraries folder and delete the old FastLED.

Install FastLED 3.0 from the FastLED releases page:
https://github.com/FastLED/FastLED/releases

**Teensy Audio Library**  
The SpectrumAnalyzer sketch requires the [Teensy Audio Library](http://www.pjrc.com/teensy/td_libs_Audio.html), which is included in [Teensyduino 1.20](http://www.pjrc.com/teensy/td_download.html).  If you have trouble compiling, first make sure you can compile either of the FastLED examples, as FastLED 3.x is also a requirement for this sketch.  If you're missing the Audio library, the best way to install is by running the Teensyduino 1.20 installer.  Make sure the "Audio" library is checked during the install, but don't check all libraries as you will downgrade FastLED to 2.0.



