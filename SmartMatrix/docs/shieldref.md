# SmartMatrix Shield

### Overview

The SmartMatrix Shield includes connectors to assemble the Shield in several configurations.

The Shield can be mounted directly to the display data connector, or separated from the display through a ribbon cable.
PHOTO

Female headers are provided so the Teensy can be removed from the shield for other projects, or can be more easily replaced if damaged.  The female headers can be omitted to make a lower profile display.
PHOTO

The shield included two connectors for power, to match the two main types of power cables included with these displays.  Select the power connector that matches your cables before assembling the kit.
PHOTO

### Shield Reference (Datasheet)

The [Teensy 3.1 specs](https://www.pjrc.com/teensy/teensy31.html) are the best source for general info on the capabilities of the Teensy 3.1 when used in the shield.  Changes from the Teensy 3.1 specs are listed below:

The shield uses 13 IO pins to drive the display, which are not brought out to the expansion header on the bottom of the shield.  The crossed off signals in the diagram are the pins used by the shield for driving the matrix display, and the remaining Teensy pins are brought out to the expansion header.
> ![Teensy Pinout](photos/TeensyPinout.png)
> Source http://www.pjrc.com/teensy/pinout.html

The current draw from the 5V (Vext) pin is limited to 500mA (assuming a 4A power supply is connected to the shield), as the display draws up to 3.5A.

Note that the 5V line may have significant ripple coming from the PWM driving of the display.  If your external circuit can handle a slightly lower voltage, using the Shield's Self Power option will give you 5V minus the voltage drop from the diode.  If your application needs closer to 5V, you can draw from the 5V line, but add a shottky diode and smoothing capacitor to your circuit. 


### Kit Assembly

Tools needed for assembling the shield

- Soldering Iron
- Solder
- Diagonal Cutters
- Wire Strippers
- Screwdriver (for Terminal Block connector only)
- X-Acto or similar Knife (for Self Power option)
- Anything on hand to raise the board off the table, for example:
    - two breadboards
    - two Post-it note pads

If soldering is new to you, this kit is fairly easy to solder as it uses all throughhole components.  This guide assumes you have the bare minimum tools, but if you have extras like a vice or third hand tool and know how to use them, please do!  The Adafruit Learning System has a [good overview on soldering](http://learn.adafruit.com/adafruit-guide-excellent-soldering/tools).

Decide how you want to connect power to the display:

- Your matrix display should have been supplied with a power cable.  There are several types that may have come with your display.  Connect the power cable to your display, and look at the other end of the cable.
- If you have the 4-pin 0.156" female connector, you want to solder the 4-pin 0.156" male connector to your board, so set the terminal block connector aside.  
- If you have another style of connector, you will need to cut off the end of your cable, strip the wires, and connect to the terminal block.  In that case, set the 4-pin 0.156" header aside.

- Decide how you want to attach the shield to the display.  The shield can be attached directly to the display connector, or can separated from the display using a ribbon cable that should have been included with your display.  Choose which connector you want to use and set the other aside.

- Decide if you want to be able to be able to remove your Teensy 3.1 from the shield, for use with another circuit.  If so, you will solder the two female headers to the board.  If not, set the headers aside.

- Finally, decide if you want to power your Teensy from USB, or from the external power supply.  
    - Powering from USB (USB Power Option) requires a USB cable to connect the Teensy to power any time you want to use the display, even if your sketch does not require USB communication with your computer.  
    - To allow for power from an external power supply (Self Power Option), you need to cut a trace on the Teensy with a knife to disconnect USB power.  If you plan on removing the Teensy from the shield later for use with another project, you will need to either solder a jumper to reconnect USB power to the Teensy, or to supply external power to the Teensy in your project.  
    - If you're using USB power, set aside the diode.

Solder pieces in the order listed below.  Solder only one or two pins first, then flip the board over and check the connector to make sure it was seated properly before continuing with the rest of the pads on the connector.

If you plan to use an I2C connector in your circuit, solder the resistors first.  If you're not sure, set them aside and you can always add them later on.  Two of the resistors pads are very close together, but they are connected to the same circuit, so don't worry if the leads touch or you have a solder blob between the two pads.  After soldering, trim the excess leads using the diagonal cutter.

If you are doing the self power option, solder the diode next.  The diode is polarized; make sure the white band around the diode matches the band on the silkscreen.  After soldering, trim the excess leads using the diagonal cutter.

If you are soldering the female headers so the Teensy is removable, solder those next.  Rest the board on top of the headers on your workspace to make a platform to solder on, and make sure the headers are upright, not bent.  Solder one joint on the end of each header, on the side next to R1/R2 to avoid the ground pin which takes longer to solder cleanly.  Flip the board over and inspect to make sure the connectors are straight and even, then flip back over and solder the remaining pins.  If anything is crooked, just melt the one solder joint to reseat the connector and inspect again.

If you are connecting the display using the shrouded header and ribbon cable, add that to the *top* of the board now.  If instead you're connecting the shield directly to the display using the female header, add that connector to the *bottom* of the now.

The rest of the soldering for these connectors is the same, but please compare your board and the pictures here before soldering more than one or two pins as it's going to be really difficult to correct later.

Flip the board over and rest on your workspace, making sure the connector is even.  Solder pin 2 (right next to the square pad), and the pin diagonally across from it.  Flip over and inspect that it's even and that it matches the pictures here.  If anything is crooked, just melt the solder joints to reseat the connector and inspect again.  Now solder the rest of the pins.

Add the 15-pin expansion header next.  You can add the connector to the top or bottom of the board depending on how you plan to connect the Shield to the rest of your project.  You can also leave the connector off if you have no plans to use it.  Add the connector to the board and hold it with your fingers well on one end.  Solder the pin at the other end.  Inspect that the connector was seated properly, and if not, melt the joint to reposition and inspect again.  When seated properly, solder the rest of the pins.

Add the external power jack next, flip the board and rest it on top of the power connector on your workspace.  Solder the middle pad first, as it is not connected to anything on the board and will heat up much easier than the other pads.  Flip the board over and make sure the connector is seated properly, and solder again if not.  Now solder the rest of the pads.  These pads are connected to large ground planes on the board and will take some time to heat up.  Try to make good contact between the soldering iron tip and the connector as well as the pad.  Adding a little extra solder to the tip before touching the pad may help transfer heat better.  When you are able to easily add solder to the joint, you know it is heated up properly.  Add plenty of solder to fully cover the joint.

Finally, add the power connector for the display.  If using the terminal block, it will be a little simpler to solder.  Just make sure the openings for the screw terminals are facing to the outside of the board, and use the same tips from above for soldering the external power jack, as these pads are connected to the same large copper planes.  

If soldering the 4-pin power connector, you need to be a little careful in positioning the connector, and may consider holding it in place with a finger on the opposite side of the connector from where you are soldering.  Add a bit of solder the first pin to hold the connector in place.  Now hold the board, pinching the connector to move it in place and melt that same bit of solder, until the connector is seated properly.  Now solder the rest of the pins, patiently heating up each pad until the solder flows easily into the joint.  Heat up the first joint again and make sure enough solder is around the pad, and it has melted properly.

If you added the female headers before, insert the two 14-pin connectors and the Teensy on top, and solder all the pads.

If you are soldering the Teensy directly to the shield, it's easier to add the header to the Teensy first.  You can use a breadboard to help hold the pins upright while soldering to the Teensy, or just rest the Teensy on top of the pins on your workspace, with a piece of cardboard added to prevent burning the top of your workspace.  Solder one pin on each header, inspect to make sure the pins are straight and even, and fix if not.  Now solder the rest of the pins.  Add the Teensy to the Shield, and pinch the Shield and Teensy together while the soldering the two pins next to R1/R2, keeping your fingers well away from the pins being soldered.  Inspect to make sure the Teensy is sitting properly on the board, fix if not, then solder the rest of the pins.  You may want to trim the pins using a diagonal cutter so they are shorter and out of the way.

