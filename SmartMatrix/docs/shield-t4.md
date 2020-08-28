# SmartLED Shield for Teensy 4

Note: right now this is just a copy of the SmartLED Shield for Teensy 3 (V4) assembly instructions, this will be updated for the Teensy 4 shield before shields start shipping

## Overview

SmartLED Shield V4 for Teensy 3 is a complete redesign of the SmartMatrix Shield.  Its new design comes as a pre-assembled board and can be used without any soldering, and it adds support for the Teensy 3.5/3.6, as well as driving APA102 LEDs.

The shield was renamed "SmartLED" from "SmartMatrix" as the new APA102 LED support can be used with LED Strips, and not just matrices.

> ![SmartLED Shield V4](photos/sdv4isometric.jpg)
> Photo courtesy Adafruit

The SmartLED Shield is available for purchase from [Adafruit](https://www.adafruit.com/products/1902) and [SparkFun](https://www.sparkfun.com/products/15046).  Compatible RGB matrix panels are available from Adafruit and linked from their SmartMatrix Shield product page.

> [Buy Shield From Adafruit >](https://www.adafruit.com/products/1902)
> [Buy Shield From SparkFun >](https://www.sparkfun.com/products/15046)

### New Features

- Teensy 3.5/3.6 support in addition to existing Teensy 3.1/3.2 support (note Teensy LC is not supported)
- Fully SMT design comes preassembled
- Teensy is removable from board
- APA102 LED support, with 5V level shifting buffers and a cable ready to plug into the JST-SM connectors used on the Adafruit DotStar panels
- Support for /32 panels (a new version of panel that has 1/32 multiplexing requiring a 5th Address pin).  e.g. [this 2.5mm pitch 64x64 pixel panel](https://www.aliexpress.com/item/p2-5-led-display-module-2-5mm-pixel-indoor-rgb-full-color-led-display-1-16/32533038333.html)
- Improved method of driving address lines on panels, saving 4 GPIO pins on the Teensy

### Other Changes from SmartMatrix SD Shield V3

- MicroSD card connector removed.  This connector takes up a lot of space and is redundant when used with the Teensy 3.5/3.6.
- Barrel jack removed and power going to the LEDs does not flow through the shield.  This keeps the shield compact, and prevents the shield from becoming a bottleneck for larger panel setups.  Supply power through the JST SM cable (or USB) instead.  
- Single breakout signal row replaced with two rows on sides of Teensy.  You can now use jumper wires or long header pins to connect to Teensy signals, and this keeps the shield more compact.

### Full Kit Contents

- SmartLED Shield V4
- Male 4-pin JST SM Cable (10cm)
- 2x8 Extra Long Pin Header

> ![SmartLED Shield Kit Contents](photos/SmartLedShieldV4Assembly/sdv4isometric-allparts.jpg)

## Specs

The [Teensy specs](https://www.pjrc.com/teensy/techspecs.html) are the best source for general info on the capabilities of the Teensy 3 when used in the shield.  Changes from the Teensy 3 specs are listed below:

The shield uses 9 IO pins to drive the display.  The crossed off signals in the diagram are the pins used by the shield for driving the matrix display, and the remaining Teensy pins are brought out to the expansion header.  On the Teensy 3.5/3.6 which have more pins, the extra pins are not used by the SmartLED Shield.

The shield uses three pins to drive the APA102 LEDs.  See more details of how to use these pins in the APA102 section below.

> ![Teensy Pinout](photos/SmartLedV4TeensyPinout.png)
> [View Large PDF](photos/SmartLEDShieldV4TeensyPinout.pdf)  
> Original Source http://www.pjrc.com/teensy/pinout.html

The Schematic, Board Layout and Gerber Files can be found in the [SmartMatrix Github Repo](https://github.com/pixelmatix/SmartMatrix/tree/master/hardware) - files start with "SmartLEDShield_V4".

There are details on the RGB Panels on the [main SmartMatrix Shield page](shieldref.html)

## Assembly
While assembly of the SmartMatrix Shield required a soldering iron and permanently attaching your Teensy to the shield, the SmartLED Shield (V4) only requires that your Teensy have pins soldered to it.  Power needs to be connected, which can be handled with crimps and/or screw terminals if you'd prefer not to solder.

### Teensy
If your Teensy doesn't come with headers pre-soldered, you need to solder them yourself.  (Note: some Teensy sellers e.g. [PJRC](https://www.pjrc.com/store/teensy36_pins.html) and [SparkFun](https://www.sparkfun.com/categories/356) sell the Teensy with pins already attached)  For the longer Teensy 3.5 and Teensy 3.6, consider soldering shorter headers if you don't plan to use the extra pins on the long end of the Teensy so the extra pins don't get in the way.  You can solder just the top 14 pins on each side, matching the length of the Teensy 3.2 and the number of holes on the SmartLED Shield.

If you need the extra pins on the Teensy 3.5/3.6, you'll have to break off one of the mounting tabs of the SmartLED Shield which is in the way of the longer row of pins.  The mounting tabs are perforated, and easy to break off with pliers.

> ![Use Pliars to break off tab](photos/SmartLedShieldV4Assembly/breakofftab1.jpg)
> ![V4 shield with tab missing](photos/SmartLedShieldV4Assembly/breakofftab2.jpg)

You can also consider adding straight or even right-angle pins to the top of the Teensy 3.5/3.6, if you want to access the extra signals from the top of the Teensy

> ![Teensy 3.6 Alternate Pins](photos/SmartLedShieldV4Assembly/Teensy36AltPins.jpg)

Note the orientation of the Teensy, the USB connector is on the same side as the 4-pin JST SM cable.  The Teensy plugs onto the "flat" side of the board, with pins going through the board.

> ![Teensy 3 Insertion](photos/SmartLedShieldV4Assembly/TeensyInsert.jpg)

### Power
The SmartLED Shield needs a 5V power connection for powering the Teensy, level shifting buffers, and any other accessories you want connected to your Teensy (e.g. microSD card, RTC module).

Your LED matrix panel needs a much higher current power connection to drive power-hungry LEDs, especially if you're using a large panel.  Think about how you're going to supply power to the panel(s) first, then think about how to tap into that power source for the SmartMatrix Shield.

Note: you can't use the 16-pin HUB75 connector on the LED matrix panel for power, as that is a data connection only, there's no access to power.

Note change from previous SmartMatrix Shields: With SmartLED Shield (V4), power going to the LEDs does not flow through the shield.  This keeps the shield compact, and prevents the shield from becoming a bottleneck for larger panel setups.

You can supply power to the SmartLED Shield and Teensy through the Teensy's USB connector, but that has some downsides.  It's usually better to supply power through the rainbow colored 4-pin female JST SM cable.    The matching 4-pin male JST SM cable is supplied in the package to make it easier to connect up to power.  

On the 4-pin JST SM Cable, the Red wire needs to be connected to 5V, and the Black wire to Ground.

Several options to connect power to the shield:

- USB
    - This is probably the easiest way to connect power to the shield, but has some downsides
    - You need a USB connection to your computer to program the Teensy, so you'll probably make this connection anyway when getting started
    - When you want to disconnect your computer and let the sketch on the Teensy run on its own, there's no more power applied to the shield, so now you need to plug in the USB cable to a USB power supply.  You'll have two 5V power supplies - one for the panel, one for the shield - in this scenario.
    - The USB connection is a bit fragile; you could accidentally pull the micro USB connector off the Teensy if you put too much stress on the connector or attached USB cable when moving a project around.
    - > ![Teensy Powered through USB](photos/SmartLedShieldV4Assembly/powerThroughUsb.jpg)
- Crimps and Barrel Jack with Screw Terminals
    - You can add fork crimps to the JST SM male cable, and now it's easy to screw both the panel crimp and shield crimp cables into a screw terminal barrel jack
    - You may want to cut the ends off or tape over the exposed JST SM cable green/yellow wires to avoid causing shorts
    - > ![Fork crimps in barrel jack screw terminal](photos/SmartLedShieldV4Assembly/forkCrimp1.jpg)
    - > ![Fork crimps in barrel jack screw terminal](photos/SmartLedShieldV4Assembly/forkCrimp2.jpg)
- Crimps, Screw Terminals, and Barrel Jack
    - Optionally add crimp to JST SM male cable's red and black wires
    - Add jumper wire to barrel jack
    - Screw panel, barrel jack wires, JST SM to screw terminal making sure all 5V wires are connected, and all Ground wire are connected
    - You may want to cut the ends off or tape over the exposed JST SM cable green/yellow wires to avoid causing shorts
    - > ![Terminal Block](photos/SmartLedShieldV4Assembly/terminalblock1.jpg)
    - > ![Terminal Block](photos/SmartLedShieldV4Assembly/terminalblock2.jpg)
- Solder JST SM male to panel
    - You can solder the red and black wires of the JST SM male cable to the 5V and GND connections on your matrix panel
    - This connection is a bit risky as it involves soldering a wire to your matrix panel.
    - The VCC (5V) and GND terminals connect to large power planes on the matrix panel PCB, and will take a powerful soldering iron and/or a long time to heat up the joint long enough to melt solder.
    - You may want to cut the ends off or tape over the exposed JST SM cable green/yellow wires to avoid causing shorts
- Special case: LED strip
    - If you're connecting APA102 LEDs in parallel or instead of the HUB75 matrix, power and ground from the JST SM cable will connect power and ground on the APA102 strip/matrix, and will power the Teensy and shield.
    - > ![Shield powered from APA102](photos/SmartLedShieldV4Assembly/poweredFromAPA102.jpg)



If you're powering the panel externally, it's recommended that you cut the VUSB trace on the Teensy to avoid accidentally back-powering the panel through the data lines when the Teensy is connected via USB.  

First, use your multimeter to do a continuity test between these two gold pads on the back of the board.  The meter should beep showing these pads are connected.  

These pads connect the 5V power line coming from USB to the Vin pin on the Teensy.  If the trace is not cut, it's possible that current could flow from the external power supply *into* to the 5V power line on your computer, or that USB will try to power the matrix panel through the data lines, potentially drawing more than the allowed amount of current from the USB power source.

> ![Teensy Vusb Cut](photos/SdAssembly/04-IMG_6158.jpg)
> Source: http://www.pjrc.com/teensy/card5b_rev3.pdf

Now, use your sharp knife to cut several times in the space between the two pads, separating the trace that connects these two pads.  Use the meter again on the two pads and listen for no beep.  If there is a beep, cut again and test.

### Data connection
In many cases, you can plug the SmartLED Shield directly into the 16-pin HUB75 connector on the panel.  This connection is convenient but not the most stable as the connectors are the only thing keeping the shield in place with only a ~4mm overlap.

The data connector on the underside of the SmartLED Shield is 2x10 pins, not 2x8 pins, on purpose to make it easier to accurately fit into the 16-pin HUB75 connector which have extra space to the top and bottom.  (With a 2x8 pin connector on the shield, it would be easy to accidentally insert the shield offset by one pin length, and potentially cause damage when power is applied.)  Occasionally the 2x10 connector will be too large for the HUB75 connector and you can either cut out the ends of the HUB75 connector or use the ribbon cable to connect.

> ![Shield Inserting to Panel](photos/SmartLedShieldV4Assembly/panelInsert.jpg)
> ![Shield Directly Attached to Panel](photos/SmartLedShieldV4Assembly/panelInsert2.jpg)

To use a ribbon cable to connect the SmartLED Shield to the matrix panel from a distance - where you can also use the mounting holes - use the included 2x8 male-male header.  Insert the pins into the top of the SmartLED Shield.  Note the red conductor on the red ribbon cable, and match that up with the "RED WIRE" text on the top of the shield.

> ![Attaching Ribbon Cable](photos/SmartLedShieldV4Assembly/ribbonInsert.jpg)
> ![Shield Connected to Panel with Ribbon Cable](photos/SmartLedShieldV4Assembly/ribbonToPanel.jpg)

### APA102 LEDs
You can connect up a strip or matrix of APA102 LEDs to the SmartLED Shield using the 4-pin JST SM connector.  The APA102 LEDs can be connected in parallel with or instead of the HUB75 connection to a panel.  You can use the APA102 strip to power the SmartLED Shield and Teensy, but not the other way around.

- DAT is connected to Teensy pin 7
- CLK is connected to Teensy pin 13
- VEXT/+5V is used to supply 5V from the APA102 strip to the SmartLED Shield
- The LED_EN signal (Teensy pin 17) must be driven high to enable the APA102 LED Buffers

See the `FastLED_Panel_Plus_APA` sketch in the SmartMatrix Library for an example of driving the APA102 LEDs with the SmartMatrix Shield

### Attaching Accessories to Teensy
The Teensy plugs into a pair of double-row connectors, giving convienient access to the main 28 pins of the Teensy to connect to other circuits by using the rows just next to the Teensy.  You can plug in male jumper wires to the extra set of holes on the side of the Teensy for easy prototyping.  You can add extra long header pins to these rows to bring the pins out for probing or connecting via female jumper wires, either from the top or bottom.  Extra long header pins on the bottom side might work well for a breadboard connection.  If you want a more secure connection, wires or pins can be soldered to the exposed pads on the top rows.  You may consider using right angle headers, soldered from the top, then optionally bent vertical to stay out of the way.

Note that some of the Teensy signals are reserved for driving the panel (see the Teensy Pinout diagram under "Specs" above).  If you are not using the APA102 drivers, those three pins can be used for other purposes.

> ![Inserting Extra Long Headers](photos/SmartLedShieldV4Assembly/extraLongHeaders.jpg)
> ![Inserting Male Jumper Wires](photos/SmartLedShieldV4Assembly/insertingJumperWires.jpg)

## Compiling and Running a SmartMatrix Sketch

See the README hosted in the [SmartMatrix GitHub Repo](https://github.com/pixelmatix/SmartMatrix/) for installation instructions.

Important note for SmartLED Shield V4: This line needs to be included before (or instead of) `#include <SmartMatrix3.h>`

```
#include <SmartLEDShieldV4.h> // this line must be first
#include <SmartMatrix3.h> //optionally include this line for SmartLED Shield V4
```

If this line isn't included, the SmartMatrix Library will assume you're using a SmartMatrix Shield V3 or earlier, which is incompatible with SmartLED Shield V4 and will result in a blank screen on your matrix.
