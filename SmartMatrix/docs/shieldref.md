# SmartLED Shield (formerly SmartMatrix Shield) Overview

## Overview

The SmartLED Shield (formerly SmartMatrix Shield) is the best way to connect the Teensy 3 to compatible Large RGB LED matrix display panels.  The shield makes it easy to connect the 13 signals required to drive the display, connects an external 5V supply to power the display and Teensy, and brings out the Teensy's free signals to a convenient header.   The kit includes several connector options for power and data, so you can connect the shield to the panel in the best way for your particular project. 

> ![SmartLED Shield Shield](photos/sdv4isometric.jpg)
> Photo courtesy Adafruit

The SmartLED Shield is available for purchase from [Adafruit](https://www.adafruit.com/products/1902).  Compatible RGB matrix panels are available from Adafruit and linked from their SmartMatrix Shield product page.

[Buy from Adafruit >](https://www.adafruit.com/products/1902)

## Versions

### SmartLED Shield V4

SmartLED Shield V4 is a complete redesign of the SmartMatrix Shield.  Its new design comes as a pre-assembled board and can be used without any soldering, and it adds support for the Teensy 3.5/3.6, as well as driving APA102 LEDs.

The shield was renamed "SmartLED" from "SmartMatrix" as the new APA102 LED support can be used with LED Strips, and not just matrices.

> ![SmartLED Shield Shield](photos/sdv4isometric.jpg)
> Photo courtesy Adafruit

[Learn More >](shield-v4.html)

### Retired: SmartMatrix SD Shield (V2 and V3)
The SmartMatrix SD Shield had a microSD card slot for storing Animated GIFs, a lower profile, and brought more signals out to the expansion connectors.  This kit required soldering to put together.

> ![SmartMatrix SD Shield](photos/sdv3isometric.jpg)
> SmartMatrix SD Shield V3 - Photo courtesy Adafruit

[SmartMatrix SD V3](shield-sdv2.html) added buffers on all the signals going to the panel for better compatibility with some panels that require 5V signals.

[SmartMatrix SD V2](shield-sdv2.html) was the version included in the [SmartMatrix Bundle](fullbundle.html), and was previously available in our Tindie store.

[SmartMatrix SD V1](shield-sd.html) was sold at Maker Faire NYC 2014 and in our Tindie store.

### Retired: SmartMatrix Shield
[SmartMatrix Shield](shield-v1.html) was sold through Adafruit and PJRC (and some of Adafruit's distributors) through May 2015.

> ![SmartMatrix Shield](photos/ProtoIsometric.jpg)
> SmartMatrix Shield

## Assembly Instructions

If you purchased a SmartMatrix product and are not sure where to go for instructions, look for a short "pixl.mx" URL on the board or packaging that will take you directly to one of the above links.

## Technical Details

### Large RGB LED Matrix Display Panels

The supported RGB matrix display panels are designed to be used in large scale video advertising screens, and come in different sizes and pixel pitches, with driver circuitry built into the board.  The panels require an external controller to refresh the display.

> ![Display Variations (Front)](photos/DisplayVariationsFront.jpg)  
> 6mm pitch 16x32, 5mm pitch 32x32, 6mm pitch 32x32

There doesn't seem to be an official standard for these displays, but they usually have the same 2x8 connector and "HUB75" pinout for connecting to a controller board.  Power is supplied to the displays through a separate connection: either two screw terminals, or a 4-pin 0.156" spacing connector.

> ![Display Variations (Back)](photos/DisplayVariationsBack.jpg)
> ![Display Pinout](photos/DisplayPinout.jpg)

There are many suppliers of RGB displays with this pinout.  The SmartMatrix Library supports driving 16x32 displays with 1/8 scan, 32x32 and 64x32 displays with 1/16 scan, and 64x64 panels with 1/16 and 1/32 scan.  Popular sources for these displays in the Maker Community are Adafruit and Sparkfun, links below.  
<br/>
[Adafruit Search for RGB LED Matrix Panels](https://www.adafruit.com/?q=rgb%20LED%20matrix%20panel)  
[Sparkfun Search for RGB LED Matrix Panels](https://www.sparkfun.com/search/results?term=RGB+LED+matrix+panel)  
<br/>
The SmartMatrix Library and SmartMatrix Shield has been tested with many panels from Adafruit and SparkFun, as well as Chinese vendors.  If you're unsure of compatibility, please post a link to the panel you're interested in to the [SmartMatrix Community](https://community.pixelmatix.com)

The displays are also available directly from suppliers in China using [Aliexpress.com](http://www.aliexpress.com/).  Search for "P4", P5", or "P6" referring to the 4-6mm pitch between LEDs and "Indoor RGB" to pull up a lot of results.  The prices may be a bit cheaper, but you will not get the same customer service as you would from Adafruit or Sparkfun, and you may get a [defective display](https://plus.google.com/113700969348903612932/posts/dmweg9newJa), or a [display that is incompatible](https://muut.com/pixelmatix#!/support:mirrored-text-start-coord) with the SmartMatrix Library, without a good way to return them.

Currently the SmartMatrix Library has support for 64x64, 64x32, 32x32, and 16x32 panels, though most of the included examples and projects based on the library are optimized for 32x32 panels and some functionality is not available for 16x32 panels.  These panels are designed to be chained together, and SmartMatrix Library supports this, though the RAM and CPU speed of the Teensy microcontroller you choose may limit your display size.

There are some high pixel density panels, e.g. 64x64 with 2.5mm pitch, that have only "A" and "B" address lines despite being specified as /32 scan (normally should have 5 address lines "A,B,C,D,E").  They use a shift register for updating the address, instead of directly driving the address lines.  These panels are not compatible with the SmartMatrix or SmartLED Shields, or the SmartMatrix Library, and are unlikely to be supported anytime in the future.

Panels with a FM6126A chipset require a special initialization sequence to be sent before starting SmartMatrix Library.  This is not yet supported by SmartMatrix Library, but there is some discussion on how to make this work [here](https://community.pixelmatix.com/t/smartmatrix-doesnt-support-fm6126a-driver-chips/421/)

Some panels drive more than one row per RGB channel at a time, and are more difficult for SmartMatrix Library to refresh.  If running example code on your panel results in scrambled text and graphics being displayed, you might have one of these panels.  These panels are only supported in the unreleased branch of the SmartMatrix Library, available [here](https://github.com/pixelmatix/SmartMatrix/tree/teensylc).  The [MultiRowRefreshMapping sketch](https://github.com/pixelmatix/SmartMatrix/tree/teensylc/examples/MultiRowRefreshMapping) in that branch walks you through determining the mapping for your panel, how to add the mapping to SmartMatrix Library, and how to test to make sure the mapping is applied correctly.  This is not yet an easy process.  You may find that one of the already added panel types supports your panel.  Feel free to record video of running the MultiRowRefreshMapping sketch and post to the [SmartMatrix Community](community.pixelmatix.com) to get help with mapping a new panel.

### Power

Connect power to the board through the 5.5mm OD, 2.1mm ID positive tip barrel jack connector.  This connector is a common size in power supplies and Adafruit seems to have standardized on it.

The display draws up to 3.5A at 5V when displaying full white.  A 5V 4A DC adapter is recommended for powering the display and Teensy.  Adafruit sells one [here](http://www.adafruit.com/products/1466).  Sparkfun did not carry a suitable power supply when I checked.

For some reason both Adafruit and Sparkfun say these panels draw only 2A max, which isn't correct.  Here's an article that shows some power supply current measurements for these panels:  
[Octoscroller - NYC Resistor](http://www.nycresistor.com/2013/09/12/octoscroller/)

Both the 16x32 and 32x32 panels will have similar current draw, which may seem strange at first examination, but both panels only light up two rows at a time when refreshing (one in the top half and one in the bottom half).  At any moment in time, either display will only have up to 64 LEDs lit at once.  The 16x32 panel scans through eight row pairs per frame, and the 32x32 panels scans through 16 row pairs per frame.  The 32x32 panel refreshes twice the number of rows, but spends half the amount of time driving each row.

### Manually Connecting Teensy and Panel

A Teensy 3 can be connected to the display panel using individual wires.  Follow the wiring for the 13 signals between J1 and U1 in the [SmartMatrix Shield schematic](https://github.com/pixelmatix/SmartMatrix/raw/master/hardware/SmartMatrixShield_V1_sch.pdf), as well as ground.  Make sure to connect the LATCH signal to both pins on the Teensy, as well as the display connector.
> ![Manual Wiring](photos/TeensyManualWiring.jpg)

Most panels are compatible with 3.3V signals, but some are not.  Starting with V3, the SmartMatrix Shield includes 74AHCT245 buffers for all the signals going to the panel, to boost the signals closer to the 5V level some panels require.  If you are seeing flickering or no LEDs lit when driving a panel, you may need to add buffers between the Teensy and panel.

If you want to use the improved circuit included in SmartLED Shield V4, that requires some external chips to drive the ADDX lines, freeing up more pins and other resources on the Teensy for other purposes.  See the [schematic](https://github.com/pixelmatix/SmartMatrix/raw/master/extras/hardware/SmartLEDShield_V4_sch.pdf) and [BOM](https://github.com/pixelmatix/SmartMatrix/raw/master/extras/hardware/SmartLEDShield_V4_BOM.pdf) for the circuit and parts needed.
