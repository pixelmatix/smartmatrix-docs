# Assembling SmartMatrix Kit

### Assembly Overview

Tools needed for assembling the shield

- Soldering Iron
- Solder
- Diagonal Cutters
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
- Finally, decide if you want to power your Teensy from USB, or from the external power supply.  Powering from USB requires a USB cable to connect the Teensy to power any time you want to use the display, even if your sketch does not require USB communication with your computer.  To allow for power from an external power supply, you need to cut a trace on the Teensy with a knife to disconnect USB power.  If you plan on removing the Teensy from the shield later for use with another project, you will need to either solder a jumper to reconnect USB power to the Teensy, or to supply external power to the Teensy in your project.  If you're using USB power, set aside the diode.

Solder pieces in order, solder one or two pins and check for seated connector before continuing

resistors and diode first

If soldering female headers - do those first
tack two legs (not on power/gnd side) and then inspect for even placement, then solder remaining pins

shrouded header is next
- approx same height as female
- if no female headers, use this as platform
- solder pin 2 and diagonal opposite (none are ground)

expansion header next

solder matrixpower next  possible to rest on shrouded/female/expansion header

solder external power connector:
rest board on top of connector, then apply solder to outside pad, just enough to hold it in place
inspect, then flip over and solder rest of pads
be sure to reflow outside pad





TODO: Decide on order based on various heights and easiest to solder 

- 4-pin power before teensy

Final inspection
