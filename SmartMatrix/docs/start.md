# SmartMatrix Overview

### Introduction
The SmartMatrix Shield is the best way to connect the Teensy 3.1 to compatible Large RGB LED matrix display panels, and in combination with the SmartMatrix Library can create stunning LED visuals with just a few lines of code.

> ![Aurora Demo](photos/AuroraDemo.jpg)
> Example display created using the SmartMatrix SD Shield, 32x32 P6 LED Matrix Panel, and SmartMatrix Frame Kit installed in a shadowbox picture frame.  
> [Click for Video](https://www.youtube.com/watch?v=alcExtbLE3w&feature=youtu.be)

The Shield is available for purchase from [Adafruit](https://www.adafruit.com/products/1902) and [PJRC](http://www.pjrc.com/store/smartmatrix_kit.html).  Compatible RGB matrix panels are available from Adafruit and linked from their SmartMatrix Shield product page.

> ![SmartMatrix Shield](photos/ProtoIsometric.jpg)

The SmartMatrix SD Shield was announced at World Maker Faire in September and will be available soon.  This new shield adds a MicroSD card reader on the board, making it easy to play animated GIFs from the card on the matrix display.  The SD Shield does not replace the SmartMatrix Shield, but is a premium option that makes it much easier to add a micro SD card to a SmartMatrix project and connect to other devices as well.  [Join the waitlist](https://www.tindie.com/products/Pixelmatix/smartmatrix-sd-shield/) on Tindie to get notified when this new shield is available.

> ![Resistor Position](photos/SdAssembly/01-IMG_6149.jpg)

Also announced was the SmartMatrix Frame kit, adding a way to easily mount a SmartMatrix Shield or SmartMatrix SD Shield and 32x32 P6 RGB Matrix Panel in an attractive shadowbox picture frame, as in the demo photo at the top of the page.  This product will be also made avilable on Tindie, [join the waitlist](https://www.tindie.com/products/Pixelmatix/smartmatrix-frame-kit/) there to find out when it's ready to ship.

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
The SmartMatrix Shield is the best way to connect the Teensy 3.1 to compatible Large RGB LED matrix display panels.  The shield makes it easy to connect the 13 signals required to drive the display, connects an external 5V supply to p[power the display and Teensy, and brings out the Teensy's free signals to a convenient header.
> ![SmartMatrix Shield](photos/ProtoIsometric.jpg)

The SmartMatrix Shield includes multiple options for connecting the Shield to the display, using either the ribbon cable included with the display, or attaching the shield directly to the display.  The shield included two connectors for power, to match the two main types of power cables included with these displays.

See more details on the shield here:  
[SmartMatrix Shield](shieldref.html)

The Shield is available for purchase from [Adafruit](https://www.adafruit.com/products/1902) and [PJRC](http://www.pjrc.com/store/smartmatrix_kit.html).

A Teensy 3.1 can also be connected to the display panel using individual wires.  Follow the wiring for the 13 signals between J1 and U1 in the [SmartMatrix Shield schematic](https://github.com/pixelmatix/SmartMatrix/raw/master/hardware/SmartMatrixShield_V1_sch.pdf), as well as ground.  Make sure to connect the LATCH signal to both pins on the Teensy, as well as the display connector.
> ![Manual Wiring](photos/TeensyManualWiring.jpg)


### Power

Connect power to the board through the 5.5mm OD, 2.1mm ID positive tip barrel jack connector.  These connector is a common size in power supplies and Adafruit seems to have standardized on it.

The display draws up to 3.5A at 5V when displaying full white.  A 5V 4A DC adapter is recommended for powering the display and Teensy.  Adafruit sells one [here](http://www.adafruit.com/products/1466).  Sparkfun did not carry a suitable power supply when I checked.

For some reason both Adafruit and Sparkfun say these panels draw only 2A max, which isn't correct.  Here's an article that shows some power supply current measurements for these panels:  
[Octoscroller - NYC Resistor](http://www.nycresistor.com/2013/09/12/octoscroller/)

Both the 16x32 and 32x32 will have similar current draw, which may seem strange at first examination, but both panels only light up two rows at a time when refreshing (one in the top half and one in the bottom half).  The 16x32 panel scans through eight row pairs per frame, and the 32x32 panels scans through 16 row pairs per frame.  The 32x32 panel refreshes twice the number of rows, but spends half the amount of time driving each row.


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

Download the latest version of the SmartMatrix Library:  
[SmartMatrix Releases - GitHub](https://github.com/pixelmatix/SmartMatrix/releases)

Import either the "16x32" or "32x32" library depending on what resolution display you have.  If you want to work with both resolutions, import both.  See instructions from Arduino here:  
[Arduino - Libraries](http://arduino.cc/en/Guide/Libraries)

Start with the FeatureDemo Example project, included with the library.  From the Arduino File menu, choose Examples, the appropriate SmartMatrix library for your display resolution, then FeatureDemo.  

You should already have most of the correct settings to load the FeatureDemo sketch on your Teensy, from running the blink example earlier.  Under Tools, CPU Speed, make sure either 48 MHz or 96MHz (overclock) is selected.

Click the Upload button, and the sketch should compile and upload to your Teensy, and start running right away.

You can use the FeatureDemo sketch as a way to get started with your own project.  Inside loop(), find a demo section that is similar to what you want to do with your project, delete the other sections, and save it as as new sketch.
