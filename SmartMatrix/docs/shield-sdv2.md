# SmartMatrix SD Shield (V2 and V3)

## Overview
SmartMatrix SD Shields have a microSD card slot for storing Animated GIFs, a lower profile, bring more signals out to the expansion connectors, and add 5V level shifting buffers on all the panel signals (as of V3).

> ![SmartMatrix SD Shield](photos/sdv3isometric.jpg)
> SmartMatrix SD Shield - Photo courtesy Adafruit

The pinout connecting to the panel is the same on all of the Shields, so code that runs on the SmartMatrix Shield should run on the SmartMatrix SD Shield.

SmartMatrix SD Shields V2 and V3 are nearly identical except for the level shifting buffers hidden under the Teensy, so the same photos are used in these instructions.

## Specs

The [Teensy 3.1 specs](https://www.pjrc.com/teensy/teensy31.html) are the best source for general info on the capabilities of the Teensy 3.1 when used in the shield.  Changes from the Teensy 3.1 specs are listed below:

The shield uses 13 IO pins to drive the display, which are not brought out to the expansion header on the bottom of the shield.  The crossed off signals in the diagram are the pins used by the shield for driving the matrix display, and the remaining Teensy pins are brought out to the expansion header.

> ![Teensy Pinout](photos/TeensyPinout.png)
> [View Large PDF](photos/SmartMatrixShieldTeensyPinout.pdf)  
> Original Source http://www.pjrc.com/teensy/pinout.html

The current draw from the 5V (Vext) pin is limited to 500mA (assuming a 4A power supply is connected to the shield), as the display draws up to 3.5A.

Note that the 5V line may have significant ripple coming from the PWM driving of the display.  If your external circuit can handle a slightly lower voltage, using the Shield's Self Power option will give you 5V minus the voltage drop from the diode.  If your application needs closer to 5V, you can draw from the 5V line, but add a schottky diode and smoothing capacitor to your circuit. 

The SmartMatrix SD Shield is very similar to the SmartMatrix Shield.  The main difference is a MicroSD slot on the board connected to SPI with chip select on pin 15.  The expansion header uses the same pins, but the layout is changed to allow for making easier connections.

This section of the SmartMatrix Shield (V3) schematic shows the names printed on the board next to the Teensy pin number/alternate pin function.  Note that the three SPI pins and pin 15 (CS2) are connected to the microSD card slot.
> ![SD pinout](photos/SdAssemblyV2/SmartMatrixSDpinout.png)

The Schematic, Board Layout and Gerber Files can be found in the [SmartMatrix Github Repo](https://github.com/pixelmatix/SmartMatrix/tree/master/hardware) - files start with "SmartMatrixSD".

There are details on the RGB Panels on the [main SmartMatrix Shield page](shieldref.html)


## Kit Assembly

Tools needed for assembling the shield

- Soldering Iron
- Solder
- Diagonal Cutters
- Wire Strippers (14 AWG) and Small Screwdriver
- X-Acto or similar Knife
- Anything on hand to protect your workspace while soldering, e.g. a scrap piece of cardboard
- Recommended: Multimeter with Continuity Tester

If soldering is new to you, this kit is fairly easy to solder as it uses all through-hole components.  This guide assumes you have the bare minimum tools, but if you have extras like a vice or third hand tool and know how to use them, please do!  The Adafruit Learning System has a [good overview on soldering](http://learn.adafruit.com/adafruit-guide-excellent-soldering/tools).

### Assembly Options
This guide focuses on using the female connector to attach to the display panel and terminal block to connect power as this gives the cleanest look when mounting in a frame.  There will be connectors left over at the end of assembly, which you can use for another project if you like.

It's not pictured, but you can use the 4-pin 0.156" connector if your panel came with one and you'd rather not cut the cable and strip the wires.  The 4-pin connector goes on the *top* of the board.  See the original [SmartMatrix Shield assembly instructions](shield-v1.html) for pictures of soldering this connector.

The pictures in the guide are for the V2 version, V3 (the version adding level shifting buffers) assembly is identical.

### Assembly Steps
Solder pieces in the order listed below.  Solder only one or two pins first, then flip the board over and check the connector to make sure it was seated properly before continuing with the rest of the pads on the connector.

Note that the side with the MicroSD slot is the top side of the board.

#### I2C Resistors
If you plan to use an I2C connector in your circuit, and you need pull-up resistors (some I2C peripherals include pull-up resistors already) solder the resistors first.  If you're not sure, set them aside and you can always add them later on.

If you're using these pins for something other than I2C, you probably don't need or want the pull-up resistors on the pins.  If you are using I2C and your peripheral already has pull-up resistors, it shouldn't break anything, but it may slow down the maximum I2C bus speed as it will now take more current to drive a 0V signal on these lines.

> ![Resistor Position](photos/SdAssemblyV2/IMG_6578.jpg)

> ![Resistor Soldering](photos/SdAssemblyV2/IMG_6579.jpg)

After soldering, trim the excess leads using the diagonal cutter.

> ![Resistor Trimming](photos/SdAssemblyV2/IMG_6580.jpg)

#### Cut Vusb Trace
You need to modify your Teensy by cutting the Vusb trace.  First, use your multimeter to do a continuity test between these two gold pads on the back of the board.  The meter should beep showing these pads are connected.  

These pads connect the 5V power line coming from USB to the Vin pin on the Teensy.  If the trace is not cut, it's possible that current could flow from the external power supply *into* to the 5V power line on your computer, or that USB will try to power the matrix panel through the data lines, potentially drawing more than the allowed amount of current from the USB power source.

> ![Teensy Vusb Cut](photos/SdAssembly/04-IMG_6158.jpg)
> Source: http://www.pjrc.com/teensy/card5b_rev3.pdf

Now, use your sharp knife to cut several times in the space between the two pads, separating the trace that connects these two pads.  Use the meter again on the two pads and listen for no beep.  If there is a beep, cut again and test.

If you forget to cut this before soldering, not all is lost, it's possible but much more awkward to cut the trace through the little gap between the soldered Teensy and Shield.  Contact us through the links above if you're in this situation.

#### Teensy Headers
Add the two 14-pin headers and 5-pin header to the SmartMatrix Shield.

 > ![Adding Teensy Headers](photos/SdAssemblyV2/IMG_6583.jpg)

Place the Teensy upside down on top of the Shield.  At this point the Teensy will just be holding the pins straight while you solder pins on the other side of the board, and placing it upside down lets you rest it flat against your table.

 > ![Upside Down Teensy](photos/SdAssemblyV2/IMG_6586.jpg)

Now flip the shield over, and put a little pressure on the board to keep the header in place and the board from moving, while soldering the underside of the pins.

  > ![Teensy Soldering Underside 1](photos/SdAssemblyV2/IMG_6589.jpg)
  > ![Teensy Soldering Underside 1](photos/SdAssemblyV2/IMG_6590.jpg)

Flip the board back over to the top, remove the Teensy and slide it back onto the pins right-side-up.
 
There are some components that are quite close to the outer rows of pins on the Teensy.  Be careful not to short or damage anything on the board by keeping the tip of the soldering iron toward the outside of the board, and by not applying too much solder.

Solder all pins on the outside of the Teensy
 
  > ![Teensy Soldering 1](photos/SdAssemblyV2/IMG_6591.jpg)
  > ![Teensy Soldering 2](photos/SdAssemblyV2/IMG_6592.jpg)


#### Expansion Header
Add the 15-pin expansion header next.  Use the right angle header to keep a low profile to the board.

Solder one pin on the top of the board to hold the connector in place.  

  > ![Expansion Header 1](photos/SdAssemblyV2/IMG_6593.jpg)

Look at the row from the side, and if the header is not straight, melt the solder and straighten it before soldering the full row on the underside of the board.

  > ![Expansion Header 2](photos/SdAssembly/13-IMG_6286.jpg)
  > ![Expansion Header 3](photos/SdAssemblyV2/IMG_6596.jpg)

#### External Power Jack
Add the external power jack next.  Flip the board and rest it on top of the power jack on your workspace.  Solder the pin in the front of the connector that is away.  Be careful where you are touching as this pin heats up the shell on the outside.

 > ![Power Jack Placement](photos/SdAssembly/14-IMG_6288.jpg)
 > ![Power Jack First Joint](photos/SdAssembly/15-IMG_6289.jpg)

Flip the board over and make sure the connector is seated properly, and solder again if not.  

Now solder the rest of the pads.  Some pads are connected to large ground planes on the board and will take some time to heat up.  Try to make good contact between the soldering iron tip and the connector as well as the pad.  Adding a little extra solder to the tip before touching the pad may help transfer heat better.  When you are able to easily add solder to the joint, you know it is heated up properly.  Add plenty of solder to fully cover the joint.



#### Matrix Data Connector
The kit includes a 20-pin female connector, though the pads on the board only have 16 holes.  This isn't a mistake, the extra length of this connector will make sure the shield isn't misaligned on the panel.  With a 16-pin connector it is far too easy to insert the connector off by one direction.

Using needle nose pliers, pull out the two pins on each end of the connector (four pins total).  Another option is to clip these pins off, but pulling them out is cleaner.  It can be easier to pull/twist the pins out from the side than to pull straight out.

> ![Pulling Pins 1](photos/SdAssembly/16-IMG_6291.jpg)
> ![Pulling Pins 2](photos/SdAssembly/17-IMG_6293.jpg)
> ![Pulling Pins 3](photos/SdAssembly/IMG_6412.jpg)
> ![Clipping Pins 1](photos/SdAssembly/18-IMG_6294.jpg)
> ![Clipping Pins 2](photos/SdAssembly/19-IMG_6295.jpg)

Add the connector, and make sure it's on the *bottom* of the board before soldering the first pin.  Flip the board over and rest one side of the board and the connector on your workspace, making sure the connector is angled perpendicular to the board.  Solder one pin to hold the connector in place.

> ![Female Header Placement](photos/SdAssemblyV2/IMG_6600.jpg)

  Flip over and inspect that it's even and that it matches the placement pictures above.  If anything is crooked, just melt the solder joint to reseat the connector and inspect again, then solder the rest of the pins.

> ![Female Header Inspection](photos/SdAssembly/21-IMG_6300.jpg)
> ![Female Header Adjustment](photos/SdAssemblyV2/IMG_6603.jpg)
> ![Female Header Soldering](photos/SdAssemblyV2/IMG_6604.jpg)

#### Matrix Power Connector
Add the power connector for the display.  To keep the power cable out of the way, add the terminal block to the bottom side of the board, with the opening facing in.  Solder the two pads on the top of the board, and use the same tips from above for soldering the external power jack, as these pads are connected to the same large copper planes.

 > ![Matrix Power Terminal Block](photos/SdAssemblyV2/IMG_6608.jpg)
 > ![Matrix Power Terminal Block Soldering](photos/SdAssemblyV2/IMG_6609.jpg)
 
#### Diode and Resistor
These parts are in a vertical orientation because of limited space.  The diode is polarized and needs to be inserted into the board with the band on the diode on the inside of the board, matching the flat end of the diode symbol printed on  the board.  Bend one side of the lead 180 degrees, then insert into the board. 

 > ![Diode Orientation](photos/SdAssemblyV2/IMG_6624.jpg)
 > ![Diode Placement](photos/SdAssemblyV2/IMG_6625.jpg)

Add the resistor bending the leads 180 degrees like the diode.  Resistors aren't polarized, so the orientation doesn't matter.

 > ![Resistor and Diode Placement](photos/SdAssemblyV2/IMG_6627.jpg)
 > ![Resistor and Diode Placement](photos/SdAssemblyV2/IMG_6628.jpg)
 
 Flip the board over and solder the four leads, then cut the excess with diagonal cutters.

 > ![Resistor and Diode Soldering](photos/SdAssemblyV2/IMG_6630.jpg)
 > ![Resistor and Diode Trimming](photos/SdAssemblyV2/IMG_6631.jpg)

#### Trimming Leads
If you are using the SmartMatrix Frame Kit, you will want to trim the leads from the first quarter inch of the board to make it as flat as possible.  Use diagonal cutters to trim the leads on the front of the external power connector, and the first three leads of the rows for the Teensy and expansion header.

 > ![Trimming Leads 1](photos/SdAssemblyV2/IMG_6610.jpg)
 > ![Trimming Leads 2](photos/SdAssemblyV2/IMG_6611.jpg)
 > ![Trimming Leads 3](photos/SdAssemblyV2/IMG_6612.jpg)

#### Board Inspection

Take a look at all the solder joints and make sure none were skipped, or have insufficient solder, or a cold solder joint especially on the power pads that take a while to heat up.

If you have a multimeter, do a continuity test between the 5V and GND pads, as a short there could be particularly bad.

#### Panel Connection
This guide assumes you have a panel with screw terminal power connectors.  Panels may also have a 4-pin power connector, and should come with a cable with at least one 4-pin power connector.  Cut the other end of the cable and strip the wires to connect to the terminal block on the shield.  You can either use just one pair of the four wires, or twist the ends of the red wires together, and the black wires together before inserting to the terminal block.

The panels sold with the SmartMatrix Bundles have a screw terminal power connection.  Strip the wires on the ends without a connector, the wire is 14 gauge.

 > ![Panel Power Connection 1](photos/SdAssembly/28-IMG_6214.jpg)

Twist the wires to make them easy to insert into the terminal block

 > ![Panel Power Connection 2](photos/SdAssembly/29-IMG_6216.jpg)

Insert the wires, noting polarity (red is 5V, black is GND)

 > ![Panel Power Connection 3](photos/SdAssembly/30-IMG_6229.jpg)
 
 Use a screwdriver to tighten the wires to the terminal block
 
 > ![Panel Power Connection 4](photos/SdAssembly/31-IMG_6316.jpg)

Add screws to the ring terminals on the other side, and screw the terminals into the screw connectors on the panel, again noting polarity (red is 5V, black is GND)

> ![Panel Power Connection 5](photos/SdAssembly/32-IMG_6232.jpg)
> (Ignore the paperboard in this picture, it does not need to be there)

Route the power cable in a smooth curve and insert the Shield into the panel.

 > ![Panel Power Connection 5](photos/SdAssembly/33-IMG_6334.jpg)

## SmartMatrix Bundle Accessories

If you purchased parts from the SmartMatrix Bundle along with the shield, you can find instructions for using the accessories from the SmartMatrix Bundle on the [SmartMatrix Bundle page](fullbundle.html#smartmatrix-bundle-accessories).

## Compiling and Running a SmartMatrix Sketch

See the README hosted in the [SmartMatrix GitHub Repo](https://github.com/pixelmatix/SmartMatrix/) for installation instructions.
