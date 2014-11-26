# SmartMatrix Shield

## Overview

The SmartMatrix Shield is the best way to connect the Teensy 3.1 to compatible Large RGB LED matrix display panels.  The shield makes it easy to connect the 13 signals required to drive the display, connects an external 5V supply to power the display and Teensy, and brings out the Teensy's free signals to a convenient header.

> ![SmartMatrix Shield](photos/ProtoIsometric.jpg)

The SmartMatrix Shield includes multiple options for connecting the Shield to the display, using either the ribbon cable included with the display, or attaching the shield directly to the display.  The shield includes two connectors for power, to match the two main types of power cables included with these displays.

The SmartMatrix Shield is available for purchase from [Adafruit](https://www.adafruit.com/products/1902) and [PJRC](http://www.pjrc.com/store/smartmatrix_kit.html).

> ![SmartMatrix Shield](photos/ShieldRef/SmartMatrixShield_V1.png)

The SmartMatrix SD Shield features a microSD connector on board and revised expansion header.  The SD Shield is not a replacement for the SmartMatrix Shield, as the new design is more expensive to manufacture and not all users want to use an SD card for storing animations.  See more details on this new shield here: [SmartMatrix Docs - SD Shield](shield-sd.html)

> ![SmartMatrix SD](photos/SdAssembly/01-IMG_6149.jpg)

## Specs

The [Teensy 3.1 specs](https://www.pjrc.com/teensy/teensy31.html) are the best source for general info on the capabilities of the Teensy 3.1 when used in the shield.  Changes from the Teensy 3.1 specs are listed below:

The shield uses 13 IO pins to drive the display, which are not brought out to the expansion header on the bottom of the shield.  The crossed off signals in the diagram are the pins used by the shield for driving the matrix display, and the remaining Teensy pins are brought out to the expansion header.
> ![Teensy Pinout](photos/TeensyPinout.png)
> [View Large PDF](photos/SmartMatrixShieldTeensyPinout.pdf)  
> Original Source http://www.pjrc.com/teensy/pinout.html

The current draw from the 5V (Vext) pin is limited to 500mA (assuming a 4A power supply is connected to the shield), as the display draws up to 3.5A.

Note that the 5V line may have significant ripple coming from the PWM driving of the display.  If your external circuit can handle a slightly lower voltage, using the Shield's Self Power option will give you 5V minus the voltage drop from the diode.  If your application needs closer to 5V, you can draw from the 5V line, but add a shottky diode and smoothing capacitor to your circuit. 

The Schematic, Board Layout, Gerber Files, and BOM can be found in the [SmartMatrix Github Repo](https://github.com/pixelmatix/SmartMatrix/tree/master/hardware).

## Kit Assembly

_For Instructions assembling the SmartMatrix SD Shield - there is a dedicated page [here](shield-sd.html)_

Tools needed for assembling the shield

- Soldering Iron
- Solder
- Diagonal Cutters
- Wire Strippers and Small Flathead Screwdriver (for Terminal Block connector only)
- X-Acto or similar Knife (for Self Power option)
- Anything on hand to protect your workspace while soldering, e.g. a scrap piece of cardboard
- Recommended: Multimeter with Continuity Tester

If soldering is new to you, this kit is fairly easy to solder as it uses all through-hole components.  This guide assumes you have the bare minimum tools, but if you have extras like a vice or third hand tool and know how to use them, please do!  The Adafruit Learning System has a [good overview on soldering](http://learn.adafruit.com/adafruit-guide-excellent-soldering/tools).

### Decisions Before Assembling
Decide how you want to connect power to the display.  Your matrix display should have been supplied with a power cable.  There are several types that may have come with your display.  Connect the power cable to your display, and look at the other end of the cable.

If you have the 4-pin 0.156" female connector, you want to solder the 4-pin 0.156" male connector to your board.

If you have another style of connector, you will need to cut off the end of your cable, strip the wires, and connect to the terminal block.

Decide how you want to attach the shield to the display.  The shield can be attached directly to the display connector, or can separated from the display using a ribbon cable that should have been included with your display.

> ![Matrix Connector Options](photos/Assembly/MatrixConnectorOptions.jpg)
> Female Header (Left), Shrouded Male Header (Right)

Decide if you want to be able to be able to remove your Teensy 3.1 from the shield, for use with another circuit.  If so, you will solder the two female headers to the board.  

> ![Teensy Socket Options](photos/Assembly/TeensySocketOptions.jpg)

Finally, decide if you want to power your Teensy from USB, or from the external power supply.  

Powering from USB (USB Power Option) requires a USB cable to connect the Teensy to power any time you want to use the display, even if your sketch does not require USB communication with your computer.  

To allow for power from an external power supply (Self Power Option), you need to cut a trace on the Teensy with a knife to disconnect USB power.  If you plan on removing the Teensy from the shield later for use with another project, you will need to either solder a jumper to reconnect USB power to the Teensy, or to supply external power to the Teensy in your project.  

### Assembly Steps
Solder pieces in the order listed below.  Solder only one or two pins first, then flip the board over and check the connector to make sure it was seated properly before continuing with the rest of the pads on the connector.

#### I2C Resistors
If you plan to use an I2C connector in your circuit, solder the resistors first.  If you're not sure, set them aside and you can always add them later on.  

> ![Resistor Position](photos/Assembly/Resistors1.jpg)

Two of the resistors pads are very close together, but they are connected to the same circuit, so don't worry if the leads touch or you have a solder blob between the two pads.

> ![Resistor Soldering](photos/Assembly/Resistors2.jpg)

After soldering, trim the excess leads using the diagonal cutter.

> ![Resistor Trimming](photos/Assembly/Resistors3.jpg)

#### Self Power Option and Diode
If you are doing the self power option, you need to modify your Teensy by cutting the Vusb trace.  First, use your multimeter to do a continuity test between these two gold pads on the back of the board.  The meter should beep showing these pads are connected.  

> ![Teensy Vusb Cut](photos/Assembly/TeensyVusbCut.jpg)
> Source: http://www.pjrc.com/teensy/card5b_rev3.pdf

Now, use your sharp knife to cut several times in the space between the two pads, separating the trace that connects these two pads.  Use the meter again on the two pads and listen for no beep.  If there is a beep, cut again and test.

> ![Teensy Vusb Cut](photos/Assembly/SelfPower1.jpg)

Advanced users only: you can solder a SMT diode between the two disconnected pads so that your Teensy can be removed and powered via USB.  There are some details [here](http://forum.pjrc.com/threads/24776-Power-from-both-USB-and-external) on the Teensy Forums.

Now, only if you cut the Vusb trace for the Self power option, solder the diode.  The diode is polarized; make sure the white band around the diode matches the band on the silkscreen.  

> ![Diode Polarity](photos/Assembly/SelfPower2.jpg)

The Anode (side without the band) is connected to a large copper plane, so you may need to heat up this joint a little longer to get the solder to melt properly.  After soldering, trim the excess leads using the diagonal cutter.

> ![Diode Soldering](photos/Assembly/SelfPower3.jpg)
> ![Diode Trimming](photos/Assembly/SelfPower4.jpg)

#### Female Teensy Headers
If you are soldering the female headers so the Teensy is removable, solder those next.  Rest the board on top of the headers on your workspace to make a platform to solder on, and make sure the headers are upright, not bent.  

> ![Female Header Placement](photos/Assembly/FemaleHeader1.jpg)

Solder one joint on the end of each header, on the side next to R1/R2 to avoid the ground pin which takes longer to solder cleanly.

> ![Female Header Soldering](photos/Assembly/FemaleHeader2.jpg)

Flip the board over and inspect to make sure the connectors are straight and even, then flip back over and solder the remaining pins.  If anything is crooked, just melt the one solder joint to reseat the connector and inspect again.

> ![Female Header Inspection](photos/Assembly/FemaleHeader3.jpg)

#### Matrix Data Connector
If you are connecting the display using the shrouded header and ribbon cable, add that to the *top* of the board now, and align the polarization notch on the connector with the mark on the board.  

> ![Male Shrouded Header Polarization](photos/Assembly/MatrixConnector1.jpg)
> ![Male Shrouded Header Placement](photos/Assembly/MatrixConnector2.jpg)

If instead you're connecting the shield directly to the display using the female header, add that connector to the *bottom* of the board now.

> ![Female Header Placement](photos/Assembly/MatrixConnector3.jpg)

The rest of the soldering for these connectors is the same, but please compare your board and the pictures here before soldering more than one or two pins as it's going to be really difficult to correct later.

Flip the board over and rest one side of the board and the connector on your workspace, making sure the connector is angled perpendicular to the board.  Solder one pin to hold the connector in place.  Flip over and inspect that it's even and that it matches the placement pictures above.  If anything is crooked, just melt the solder joint to reseat the connector and inspect again, then solder the rest of the pins.

> ![Male Shrouded Header Soldering](photos/Assembly/MatrixConnector4.jpg)
> ![Male Shrouded Header Adjustment](photos/Assembly/MatrixConnector5.jpg)
> Male Shrouded Header Pictures

> ![Female Header Soldering](photos/Assembly/MatrixConnector6.jpg)
> ![Female Header Adjustment](photos/Assembly/MatrixConnector7.jpg)
> Female Header Pictures

#### Expansion Header
Add the 15-pin expansion header next.  You can add the connector to the top or bottom of the board depending on how you plan to connect the Shield to the rest of your project.  You can also leave the connector off if you have no plans to use it.  

Rest the board on top of the connector, using something to protect your workspace from the heat while soldering.  

Solder the pin at one end of the connector, don't worry about the connector being straight at this point.  

> ![Expansion Header Adjustment](photos/Assembly/Expansion1.jpg)

Hold the board and connector with your fingers on the end away from the solder.  Heat up the solder joint and move the connector into place with your fingers.  When seated properly, put the board back on your workspace and solder the rest of the pins.

 > ![Expansion Header Final Soldering](photos/Assembly/Expansion3.jpg)

#### External Power Jack
Add the external power jack next.  Flip the board and rest it on top of the power jack on your workspace.  Solder the middle pad first, as it is not connected to anything on the board and will heat up much easier than the other pads.  

 > ![Power Jack First Joint](photos/Assembly/ExtPower1.jpg)

Flip the board over and make sure the connector is seated properly, and solder again if not.  

 > ![Power Jack Inspection](photos/Assembly/ExtPower2.jpg)

Now solder the rest of the pads.  These pads are connected to large ground planes on the board and will take some time to heat up.  Try to make good contact between the soldering iron tip and the connector as well as the pad.  Adding a little extra solder to the tip before touching the pad may help transfer heat better.  When you are able to easily add solder to the joint, you know it is heated up properly.  Add plenty of solder to fully cover the joint.

 > ![Power Jack Final Soldering](photos/Assembly/ExtPower3.jpg)

#### Matrix Power Connector
Add the power connector for the display.  If using the terminal block, it will be a little easier to solder.  Just make sure the openings for the screw terminals are facing to the outside of the board, and use the same tips from above for soldering the external power jack, as these pads are connected to the same large copper planes.

 > ![Matrix Power Terminal Block](photos/Assembly/MatrixPower1.jpg)

If soldering the 4-pin power connector, you need to be a little careful in positioning the connector so that the pins stick up though the board while the board and connector rest on your workspace.  Don't worry about getting the alignment right when soldering the first pin, just melt enough solder to hold the connector in place.  Solder the pin on the 5V side, not ground, as the 5V plane is smaller and heats up quicker.

 > ![Matrix Power 4-Pin First Joint](photos/Assembly/MatrixPower2.jpg)

Now hold the board, and while keeping your fingers away from the one solder joint, pinch the connector to move it in place and melt that same bit of solder, until the connector is seated properly.

 > ![Matrix Power 4-Pin Adjustment](photos/Assembly/MatrixPower3.jpg)
 > ![Matrix Power 4-Pin Inspection](photos/Assembly/MatrixPower4.jpg)
 > Properly seated power connector

Now solder the rest of the pins, patiently heating up each pad until the solder flows easily into the joint.  Heat up the first joint again and make sure enough solder is around the pad, and it has melted properly.

 > ![Matrix Power 4-Pin Final Soldering](photos/Assembly/MatrixPower5.jpg)

#### Teensy Headers
If you added the female headers before, insert the two 14-pin connectors and the Teensy on top, and solder all the pads.

 > ![Adding Teensy Male Headers to Female](photos/Assembly/TeensyHeaders1.jpg)
  > ![Soldering Headers to Teensy](photos/Assembly/TeensyHeaders2.jpg)

If you are soldering the Teensy directly to the shield, it's easier to add the header to the Teensy first.  You can use a breadboard to help hold the pins upright while soldering to the Teensy, or just rest the Teensy on top of the pins on your workspace, with a piece of cardboard below to prevent burning the top of your workspace. To add the Teensy with headers to the Shield, solder one pin on each header, inspect to make sure the pins are straight and even, and fix if not before soldering the rest of the pins.

  > ![Soldering Headers to Teensy](photos/Assembly/TeensyHeaders3.jpg)

Add the Teensy to the Shield, resting the Teensy on your workspace with the board on top.  Solder the two pins next to R1/R2.  Inspect to make sure the Teensy is sitting properly on the board, fix if not, then solder the rest of the pins.  

  > ![Soldering Teensy to board](photos/Assembly/TeensyHeaders4.jpg)

You may want to trim the pins using a diagonal cutter so they are shorter and out of the way.

  > ![Trimming Teensy pins](photos/Assembly/TeensyHeaders5.jpg)

#### Final Inspection

Take a look at all the solder joints and make sure none were skipped, or have insufficient solder, or a cold solder joint especially on the power pads that take a while to heat up.

If you have a multimeter, do a continuity test between the 5V and GND pads, as a short there could be particularly bad.

