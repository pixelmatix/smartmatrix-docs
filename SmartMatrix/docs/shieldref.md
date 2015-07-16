# SmartMatrix Shield

## Overview

The SmartMatrix Shield is the best way to connect the Teensy 3.1 to compatible Large RGB LED matrix display panels.  The shield makes it easy to connect the 13 signals required to drive the display, connects an external 5V supply to power the display and Teensy, and brings out the Teensy's free signals to a convenient header.  

The SmartMatrix Shield includes multiple options for connecting the Shield to the display, using either the ribbon cable included with the display, or attaching the shield directly to the display.  The shield includes two connectors for power, to match the two main types of power cables included with these displays.

> ![SmartMatrix Shield](photos/sdv3isometric.jpg)
> Photo courtesy Adafruit

The SmartMatrix Shield is available for purchase from [Adafruit](https://www.adafruit.com/products/1902).  Compatible RGB matrix panels are available from Adafruit and linked from their SmartMatrix Shield product page.

The SmartMatrix Bundle - which comes with everything you need to build a display that can be mounted in a shadowbox picture frame and comes with a remote control to change what's playing - is available through the [Hackaday Store](http://store.hackaday.com/products/smartmatrix-bundle) with free worldwide shipping.

## Versions
### SmartMatrix SD Shield
SmartMatrix SD Shields have a microSD card slot for storing Animated GIFs, a lower profile, and bring more signals out to the expansion connectors.

> ![SmartMatrix SD Shield](photos/sdv3isometric.jpg)
> SmartMatrix SD Shield V3 - Photo courtesy Adafruit

[SmartMatrix SD V3](shield-sdv2.html) adds buffers on all the signals going to the panel for better compatibility with some panels that require 5V signals.

[SmartMatrix SD V2](shield-sdv2.html) is the version included in the [SmartMatrix Bundle](fullbundle.html), and was previously available in our Tindie store.

[SmartMatrix SD V1](shield-sd.html) was sold at Maker Faire NYC 2014 and in our Tindie store.

### SmartMatrix Shield
[SmartMatrix Shield](shield-v1.html) was sold through Adafruit and PJRC (and some of Adafruit's distributors) through May 2015.

> ![SmartMatrix Shield](photos/ProtoIsometric.jpg)
> SmartMatrix Shield

### SmartMatrix Bundle
The [SmartMatrix Bundle](fullbundle.html) comes with everything you need to build a display that can be mounted in a shadowbox picture frame and comes with a remote control to change what's playing.

> ![SmartMatrix in MCS Frame](photos/Shop/MCSFrameFront.jpg)

> ![SmartMatrix Bundle](photos/Shop/SmartMatrixBundle.jpg)


If you purchased a SmartMatrix product and are not sure where to go for instructions, look for a short "pixl.mx" URL on the board or packaging that will take you directly to one of the above links.

## Technical Details
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

### Power
Connect power to the board through the 5.5mm OD, 2.1mm ID positive tip barrel jack connector.  This connector is a common size in power supplies and Adafruit seems to have standardized on it.

The display draws up to 3.5A at 5V when displaying full white.  A 5V 4A DC adapter is recommended for powering the display and Teensy.  Adafruit sells one [here](http://www.adafruit.com/products/1466).  Sparkfun did not carry a suitable power supply when I checked.

For some reason both Adafruit and Sparkfun say these panels draw only 2A max, which isn't correct.  Here's an article that shows some power supply current measurements for these panels:  
[Octoscroller - NYC Resistor](http://www.nycresistor.com/2013/09/12/octoscroller/)

Both the 16x32 and 32x32 panels will have similar current draw, which may seem strange at first examination, but both panels only light up two rows at a time when refreshing (one in the top half and one in the bottom half).  At any moment in time, either display will only have up to 64 LEDs lit at once.  The 16x32 panel scans through eight row pairs per frame, and the 32x32 panels scans through 16 row pairs per frame.  The 32x32 panel refreshes twice the number of rows, but spends half the amount of time driving each row.


### Manually Connecting Teensy and Panel
A Teensy 3.1 can be connected to the display panel using individual wires.  Follow the wiring for the 13 signals between J1 and U1 in the [SmartMatrix Shield schematic](https://github.com/pixelmatix/SmartMatrix/raw/master/hardware/SmartMatrixShield_V1_sch.pdf), as well as ground.  Make sure to connect the LATCH signal to both pins on the Teensy, as well as the display connector.
> ![Manual Wiring](photos/TeensyManualWiring.jpg)

Most panels are compatible with 3.3V signals, but some are not.  Starting with V3, the SmartMatrix Shield includes 74AHCT245 buffers for all the signals going to the panel, to boost the signals closer to the 5V level some panels require.  If you are seeing flickering or no LEDs lit when driving a panel, you may need to add buffers between the Teensy and panel.


