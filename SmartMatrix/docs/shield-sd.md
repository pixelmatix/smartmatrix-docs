# SmartMatrix SD Shield

## Overview

The SmartMatrix SD Shield is brand new, and the documentation is even newer.  If you see any errors or have any questions, please contact us (links above), and the documentation will be improved over the coming weeks.

**Attention Maker Faire Customers** - If you bought a full frame kit on Saturday before 3 PM, you are missing a small parts bag containing four M3 screws to attach the paperpoard to the panel, and a hanger and nails to add to the frame.  Please contact us at the links above, and we'll send the missing parts to you ASAP.  If you're in the middle of assembling and don't want to wait, home depot carries this screw in store which is not identical but will work temporarily while we get the missing parts out to you: [Home Depot - M3 6mm phillips pan head screw](http://www.homedepot.com/p/Crown-Bolt-M3-6-mm-Phillips-Pan-Head-Machine-Screws-3-Pack-36618/202836120)

## Specs

The SmartMatrix SD Shield is very similar to the SmartMatrix Shield.  The main difference is a MicroSD slot on the board connected to SPI with chip select on pin 15.  The expansion header uses the same pins (with the exception of pin 15), but the layout is changed to allow for making easier connections.

The Schematic, Board Layout and Gerber Files can be found in the [SmartMatrix Github Repo](https://github.com/pixelmatix/SmartMatrix/tree/master/hardware).


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
This guide focuses on using the female connector to attach to the display panel and terminal block to connect power, as this method is what was presented at Maker Faire when this shield was released.  There will be connectors left over at the end of assembly, which you can use for another project if you like.


### Assembly Steps
Solder pieces in the order listed below.  Solder only one or two pins first, then flip the board over and check the connector to make sure it was seated properly before continuing with the rest of the pads on the connector.

Note that the side with the MicroSD slot is the top side of the board.

#### I2C Resistors
If you plan to use an I2C connector in your circuit, and you need pull-up resistors (some I2C peripherals include pull-up resistors already) solder the resistors first.  If you're not sure, set them aside and you can always add them later on.

If you're using these pins for something other than I2C, you probably don't need or want the pull-up resistors on the pins.  If you are using I2C and your peripheral already has pull-up resistors, it shouldn't break anything, but it may slow down the maximum I2C bus speed as it will now take more current to drive a 0V signal on these lines.

> ![Resistor Position](photos/SdAssembly/01-IMG_6149.jpg)

Two of the resistors pads are very close together, but they are connected to the same circuit, so don't worry if the leads touch or you have a solder blob between the two pads.

> ![Resistor Soldering](photos/SdAssembly/02-IMG_6151.jpg)

After soldering, trim the excess leads using the diagonal cutter.

> ![Resistor Trimming](photos/SdAssembly/03-IMG_6153.jpg)

You need to modify your Teensy by cutting the Vusb trace.  First, use your multimeter to do a continuity test between these two gold pads on the back of the board.  The meter should beep showing these pads are connected.  

These pads connect the 5V power line coming from USB to the Vin pin on the Teensy.  If the trace is not cut, it's possible that current could flow from the external power supply *into* to the 5V power line on your computer, or that USB will try to power the matrix panel through the data lines, potentially drawing more than the allowed amount of current from the USB power source.

> ![Teensy Vusb Cut](photos/Assembly/TeensyVusbCut.jpg)
> Source: http://www.pjrc.com/teensy/card5b_rev3.pdf

Now, use your sharp knife to cut several times in the space between the two pads, separating the trace that connects these two pads.  Use the meter again on the two pads and listen for no beep.  If there is a beep, cut again and test.

If you forget to cut this before soldering, not all is lost, it's possible but much more awkward to cut the trace through the little gap between the soldered Teensy and Shield.  Contact us through the links above if you're in this situation.

> ![Teensy Vusb Cut](photos/Assembly/SelfPower1.jpg)

#### Teensy Headers
Add the two 14-pin headers and 5-pin headers to the underside of the Teensy.

 > ![Adding Teensy Headers](photos/SdAssembly/05-IMG_6273.jpg)

Place the Teensy on top of the Shield, and rest the shield on the table, so the Shield will keep the pins straight while soldering

There are some components that are quite close to the outer rows of pins on the Teensy.  Be careful not to short or damage anything on the board by keeping the tip of the soldering iron toward the outside of the board, and by not applying too much solder.

 > ![Shield holder](photos/SdAssembly/06-IMG_6276.jpg)
 
 Solder all pins on the outside of the Teensy
 
  > ![Teensy Soldering 1](photos/SdAssembly/07-IMG_6278.jpg)
  > ![Teensy Soldering 2](photos/SdAssembly/08-IMG_6279.jpg)

Now flip the shield over, and put a little pressure on the board to keep the header in place and the board from moving, while soldering the underside of the pins.

  > ![Teensy Soldering Underside 1](photos/SdAssembly/09-IMG_6281.jpg)
  > ![Teensy Soldering Underside 1](photos/SdAssembly/10-IMG_6282.jpg)

#### Expansion Header
Add the 15-pin expansion header next.  Use the right angle header to keep a low profile to the board.

Solder one pin on the top of the board to hold the connector in place.  

  > ![Expansion Header 1](photos/SdAssembly/11-IMG_6183.jpg)

Look at the row from the side, and if the header is not straight, melt the solder and straighten it before soldering the full row on the underside of the board.

  > ![Expansion Header 2](photos/SdAssembly/13-IMG_6286.jpg)
  > ![Expansion Header 3](photos/SdAssembly/12-IMG_6284.jpg)

#### External Power Jack
Add the external power jack next.  Flip the board and rest it on top of the power jack on your workspace.  Solder the pin in the front of the connector that is away.  Be careful where you are touching as this pin heats up the shell on the outside.

 > ![Power Jack Placement](photos/SdAssembly/14-IMG_6288.jpg)
 > ![Power Jack First Joint](photos/SdAssembly/15-IMG_6289.jpg)

Flip the board over and make sure the connector is seated properly, and solder again if not.  

Now solder the rest of the pads.  Some pads are connected to large ground planes on the board and will take some time to heat up.  Try to make good contact between the soldering iron tip and the connector as well as the pad.  Adding a little extra solder to the tip before touching the pad may help transfer heat better.  When you are able to easily add solder to the joint, you know it is heated up properly.  Add plenty of solder to fully cover the joint.



#### Matrix Data Connector
The kit includes a 20-pin female connector, though the pads on the board only have 16 holes.  This isn't a mistake, the extra length of this connector will make sure the shield isn't misaligned on the panel.  With a 16-pin connector it is far too easy to insert the connector off by one direction.

Using needle nose pliers, pull out the two pins on each end of the connector (four pins total).  Another option is to clip these pins off, but pulling them out is cleaner.

> ![Pulling Pins 1](photos/SdAssembly/16-IMG_6291.jpg)
> ![Pulling Pins 2](photos/SdAssembly/17-IMG_6293.jpg)
> ![Clipping Pins 1](photos/SdAssembly/18-IMG_6294.jpg)
> ![Clipping Pins 2](photos/SdAssembly/19-IMG_6295.jpg)

Add the connector, and make sure it's on the *bottom* of the board before soldering the first pin.  Flip the board over and rest one side of the board and the connector on your workspace, making sure the connector is angled perpendicular to the board.  Solder one pin to hold the connector in place.

> ![Female Header Placement](photos/SdAssembly/20-IMG_6299.jpg)

  Flip over and inspect that it's even and that it matches the placement pictures above.  If anything is crooked, just melt the solder joint to reseat the connector and inspect again, then solder the rest of the pins.

> ![Female Header Inspection](photos/SdAssembly/21-IMG_6300.jpg)
> ![Female Header Adjustment](photos/SdAssembly/22-IMG_6302.jpg)
> ![Female Header Soldering](photos/SdAssembly/23-IMG_6303.jpg)

#### Matrix Power Connector
Add the power connector for the display.  To keep the power cable out of the way, add the terminal block to the bottom side of the board, with the opening facing in.  Solder the two pads on the top of the board, and use the same tips from above for soldering the external power jack, as these pads are connected to the same large copper planes.

 > ![Matrix Power Terminal Block](photos/SdAssembly/24-IMG_6306.jpg)

#### Trimming Leads
If you are using the SmartMatrix Frame Kit, you will want to trim the leads from the first quarter inch of the board to make it as flat as possible.  Use diagonal cutters to trim the leads on the front of the external power connector, and the first three leads of the rows for the Teensy and expansion header.

 > ![Trimming Leads 1](photos/SdAssembly/25-IMG_6307.jpg)
 > ![Trimming Leads 2](photos/SdAssembly/26-IMG_6311.jpg)
 > ![Trimming Leads 3](photos/SdAssembly/27-IMG_6313.jpg)

#### Board Inspection

Take a look at all the solder joints and make sure none were skipped, or have insufficient solder, or a cold solder joint especially on the power pads that take a while to heat up.

If you have a multimeter, do a continuity test between the 5V and GND pads, as a short there could be particularly bad.

#### Panel Connection
The panels sold at Maker Faire have a screw terminal power connection.  Strip the wires on the ends without a connector, the wire is 14 gauge.

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

## Accessories

### SmartMatrix Frame Kit

The first batch of paperboard has extra holes due to a miscommunication with the vendor.  It may take a little extra work to find the right holes.  Use the picture with the screws to see which holes to use.  Use the polarizing pins on the panel to guide the paperboard into the right place.

When routing the matrix power cable between the paperboard and the display, be careful of the sharp screws that protrude from the display.  Route the cable to avoid the screws so they do not impale the power cable when the paperboard is added.  You can also remove the screws, or clip them with diagonal cutters to be shorter and less sharp.

The shield rests on top of the paperboard at an angle.  If you want to keep the shield flat for a lower profile, you can cut the paperboard with a knife, then gently bend it down so the front of the shield can sit lower.  

> ![title](photos/SdAssembly/Frame/1-IMG_6320.jpg) 

Start with the Shield plugged (loosely is fine) into the matrix data connector and the power cable routed the way you want it.  Unplug the Shield and feed it at an angle through the hold in the paperboard. 

> ![title](photos/SdAssembly/Frame/2-IMG_6321.jpg) 
> ![title](photos/SdAssembly/Frame/3-IMG_6322.jpg) 

Seat the paperboard on the matrix panel, making sure the polarizing pins on the panel fit through holes in the paperboard, and the four screw holes in the corners are visible through other holes.

> ![title](photos/SdAssembly/Frame/4-IMG_6324.jpg) 

Make sure the cable is routed neatly under the paperboard and isn't kinked or sitting on top of a sharp screw in the panel.  Adjust the cable routing if necessary.  Press down a bit to hold the paperboard in place until you have added a screw in the upper right corner to hold it for you.  

> ![title](photos/SdAssembly/Frame/5-IMG_6326.jpg) 

Tighten each screw until the paperboard is sitting flat against the panel and the top of the screw is flush with the paperboard

> ![title](photos/SdAssembly/Frame/6-IMG_6327.jpg) 

Remove the cover from the adhesive strip

> ![title](photos/SdAssembly/Frame/7-IMG_6329.jpg) 

Insert the shield into the data connector and push the front edge down on the adhesive.  If you cut and bent down the adhesive a bit before adding the shield, the shield should sit fairly flat against the paperboard.

> ![title](photos/SdAssembly/Frame/8-IMG_6332.jpg)

#### Compatible Frames
There are quite a few 8"x8" shadow box frames out there, but only two of them are recommended for use with the SmartMatrix Frame Kit based on fit and quality.

MCS makes a 1" deep frame that gives a pixelated effect when used with the frosted acrylic in the SmartMatrix Frame Kit.  It's available from [Amazon.com](http://www.amazon.com/MCS-Scrapbook-Shadowbox-8-Inch-40393/dp/B004L6G2RE/), and [other online stores](https://www.google.com/shopping/product/8413181197040904862), and may be available at local stores.  It's MCS item number 40393.  Jeff reports some A.C. Moore stores (East Coast) carry this frame.

Michaels makes a 1-1/4" deep frame that gives an abstract effect when used with the frosted acrylic in the SmartMatrix Frame Kit.  It's available from [Michaels.com](http://www.michaels.com/shadowbox-with-signature-mat-black-8x8in/10223090.html) as well as in most of their stores.

#### MCS Frame Installation

Of the two frames, this one is the easiest to install as it doesn't require any modification or tools.

Lift up the tabs on the back of the frame to remove the MDF panel

> ![title](photos/SdAssembly/Frame/MCS/1-IMG_6241.JPG) 

Remove the MDF and paper.  We won't need these anymore.

> ![title](photos/SdAssembly/Frame/MCS/2-IMG_6243.JPG) 

Remove the divider, and carefully remove the glass as it has sharp edges.  We won't need the glass anymore either.

> ![title](photos/SdAssembly/Frame/MCS/3-IMG_6244.JPG) 

Remove the protective film from both sides of the frosted acrylic.  It may be difficult to start peeling the film, you can use the edge of a knife to separate the film from the acrylic at one of the corners to get started.  

> ![title](photos/SdAssembly/Frame/Michaels/09-IMG_6345.JPG) 

Set the acrylic into the frame

> ![title](photos/SdAssembly/Frame/MCS/4-IMG_6245.JPG) 

Hold the acrylic up to some light to look for any dust that will show up when backlit from the LEDs.  Clean off any dust before closing everything back up.

> ![title](photos/SdAssembly/Frame/MCS/5-IMG_6247.JPG) 

Add the divider back to the frame.

> ![title](photos/SdAssembly/Frame/MCS/6-IMG_6248.JPG) 

Drop the display with the paperboard panel onto the divider, and close the tabs to hold everything together.

> ![title](photos/SdAssembly/Frame/MCS/7-IMG_6249.JPG) 

This frame doesn't come with a hanger (it was on the MDF).  You can use attach the included hanger and nails to the frame if you want to mount it on the wall.

#### Michaels Frame Installation

You will need some needle-nose pliers and something thin for prying (a paint scraper for example) for installation of this frame.

Lift up the tabs on the back of the frame to remove the MDF panel

> ![title](photos/SdAssembly/Frame/Michaels/02-IMG_6336.JPG) 

Remove the MDF and paper.  We won't need these anymore.
> ![title](photos/SdAssembly/Frame/Michaels/03-IMG_6337.JPG) 

The divider is made up of four pieces nailed to the sides of the frame.  Insert something thin that can pry each piece from the side of the frame.  It doesn't take much force to separate the pieces.  

> ![title](photos/SdAssembly/Frame/Michaels/04-IMG_6339.JPG) 
> ![title](photos/SdAssembly/Frame/Michaels/05-IMG_6340.JPG) 

Set the pieces aside, we will add them back later.

> ![title](photos/SdAssembly/Frame/Michaels/06-IMG_6341.JPG) 

Now use needle-nose pliers to pull the nails from the sides of the frame.

> ![title](photos/SdAssembly/Frame/Michaels/07-IMG_6342.JPG) 

Carefully remove the glass as it has sharp edges.  We won't need the glass anymore.

> ![title](photos/SdAssembly/Frame/Michaels/08-IMG_6344.JPG) 

Remove the protective film from both sides of the frosted acrylic.  It may be difficult to start peeling the film, you can use the edge of a knife to separate the film from the acrylic at one of the corners to get started.  Set the acrylic into the frame

> ![title](photos/SdAssembly/Frame/Michaels/09-IMG_6345.JPG) 

Hold the acrylic up to some light to look for any dust that will show up when backlit from the LEDs.  Clean off any dust before closing everything back up.

> ![title](photos/SdAssembly/Frame/MCS/5-IMG_6247.JPG) 

Add the four divider pieces back to the frame.

> ![title](photos/SdAssembly/Frame/Michaels/10-IMG_6346.JPG)

Carefully drop the display with the paperboard panel onto the divider so the display panel is between the divider and the paperboard is resting on top, without knocking over any of the divider pieces.  Close the tabs to hold everything together.

> ![title](photos/SdAssembly/Frame/Michaels/11-IMG_6347.JPG)

### IR Remote Kit

(More details coming soon)

The red/black/white leads line up to 3V3/Gnd/Data pins on the IR Receiver.  Use the pictures to make sure the receiver is inserted the right way.

Wiggle and guide the leads in with pinched fingers, and push gently on the head of the receiver as well.  The leads will move in noticeably when positioned correctly.

You can braid the cable to keep it tidier.  Insert the loose ends into the 3-pin housing in the same Red/Black/White order as the other end of the cable.  Use the colors to add the IR receiver cable to the correct pins on the SmartMatrix SD Shield

The battery compartment can be tricky to open.  Use one fingernail to move the tab inward.  At the same time, use your thumbnail to pull the tray outward.  

> ![title](photos/SdAssembly/IR/1-IMG_6349.jpg) 
> ![title](photos/SdAssembly/IR/2-IMG_6351.jpg) 
> ![title](photos/SdAssembly/IR/3-IMG_6352.jpg)
> ![title](photos/SdAssembly/IR/4-IMG_6353.jpg)
> ![title](photos/SdAssembly/IR/5-IMG_6356.jpg)
> ![title](photos/SdAssembly/IR/6-IMG_6357.jpg) 
> ![title](photos/SdAssembly/IR/7-IMG_6359.jpg) 
> ![title](photos/SdAssembly/IR/8-IMG_6360.jpg) 
> ![title](photos/SdAssembly/IR/9-IMG_6363.jpg)

### Aurora Sketch

This sketch demoed at Maker Faire features a menu system controlled using the IR remote and plays animated GIFs from a SD card.  You can find the sketch and instructions for use here:
https://github.com/pixelmatix/aurora
