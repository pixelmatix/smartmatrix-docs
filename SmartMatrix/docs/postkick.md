# SmartMatrix After Kickstarter
Our Kickstarter campaign ended, but the SmartMatrix project isn't over.  We're selling the SmartMatrix units we already built, with free shipping to the US, while supplies last:

<a href="https://shop.trycelery.com/page/556bb89a502fad0b00edf08d" data-celery="556bb89a502fad0b00edf08d" data-celery-version="v2">Pre-order SmartMatrix Now ></a>
<script async type="text/javascript" src="https://www.trycelery.com/js/celery.js"></script>  

> ![SmartMatrix](photos/KickStaffPick.jpg)

Please join our list to find out when SmartMatrix is available outside the US. We'll extend a discount to non-US customers on the list when we do our wider release:  [SmartMatrix Non-US Waiting List](http://eepurl.com/bnEwKv)

If you know how to solder you can put together a SmartMatrix display yourself.  Check out our [Instructable](www.instructables.com/id/SmartMatrix-Dynamic-LED-Art-Display/), or the [shop page](shop.html) to find out where you can buy the SmartMatrix Shield.

Please join [our mailing list](http://eepurl.com/UX2V5) to get the latest updates on SmartMatrix.  [Join us in the forums](http://community.pixelmatix.com/) if you'd like to have a conversation.

## Assembling SmartMatrix

This [Assembly Video](https://vimeo.com/129599847) may help as a supplement to the pictures and text instructions.  The first few steps up through "Connect Ribbon Cable" are done already for you.

### IR Sensor Cable

The red/black/white leads line up to 3V3/Gnd/Data pins on the IR Receiver.  Use the pictures to make sure the receiver is inserted the right way.

> ![title](photos/SdAssembly/IR/1-IMG_6349.jpg) 

It can be difficult to tell how far the leads are inserted into the connector.  This sensor has the leads covered with a black marker to the depth of the connector, about .19".  When inserted properly, you can't see the black marker anymore.  This can be a good way to tell if the sensor is inserted far enough.

> ![title](photos/SdAssembly/IR/IMG_6417.jpg) 

It's much easier to insert the sensor when the leads are at an angle.  Point the leads so they are facing the all-white wall of the connector, not the side with the silver contacts visible.  Pointed this way, it should only take a little pressure and wiggling of the sensor before it goes in.  The leads will move in noticeably when positioned correctly.  

> ![title](photos/SdAssembly/IR/IMG_6419.jpg) 

You can braid the cable to keep it tidier.  

> ![title](photos/SdAssembly/IR/4-IMG_6353.jpg)

Insert the loose ends into the 3-pin housing in the same Red/Black/White order as the other end of the cable.

> ![title](photos/SdAssembly/IR/5-IMG_6356.jpg)
> ![title](photos/SdAssembly/IR/6-IMG_6357.jpg)

Slide the end of the cable between the plastic frame and the the circuit baord on the back side of the LED Matrix panel.  

> ![title](photos/KickAssembly/IMG_7411.jpg) ![title](photos/KickAssembly/IMG_7412.jpg)

Plug the cable into the 3-pin connector on the SmartMatrix board, matching the colors of the cable to the labels on the board.  Make sure to route the cable around - not on top of - the 16 pin connector on the LED Matrix panel.

> ![title](photos/KickAssembly/IMG_7416.jpg)

### Assembling Frame

Fold the tabs on the frame back and remove the back of the frame, SmartMatrix panel, divider, and frosted acrylic.

Remove the protective film from both sides of the frosted acrylic.  It may be difficult to start peeling the film, you can use the edge of a knife to separate the film from the acrylic at one of the corners to get started.  

> ![title](photos/SdAssembly/Frame/Michaels/09-IMG_6345.JPG) 

Set the acrylic into the frame

> ![title](photos/SdAssembly/Frame/MCS/4-IMG_6245.JPG) 

Hold the acrylic up to some light to look for any dust that will show up when backlit from the LEDs.  Clean off any dust before closing everything back up.

> ![title](photos/SdAssembly/Frame/MCS/5-IMG_6247.JPG) 

Add the divider to the frame

> ![title](photos/KickAssembly/IMG_7422.jpg)

Set the MDF back of the frame, holding the IR sensor cable and making sure the cable is not pinched between the plastic and MDF.  The rounded dome of the IR sensor should be facing down toward the table.

> ![title](photos/KickAssembly/IMG_7417.jpg)

Add the screws loosely to the panel.  It may take a little effort to push the MDF into position so the screws align, and you probably need to hold the MDF in place with one hand while adding the first screws.  In two corners, there are plastic alignment pins that need to go through the MDF.  Align those pins with the MDF and add the adjacent screws first.

> ![title](photos/KickAssembly/IMG_7419.jpg)

Check the panel and MDF from the side to make sure they are fitting together, and there's nothing pinched between the panel and MDF.  On the side with the IR sensor, there will be a little gap where the SmartMatrix board screws and IR sensor push on the MDF a little bit.

> ![title](photos/KickAssembly/IMG_7420.jpg)
> ![title](photos/KickAssembly/IMG_7421.jpg)

Drop the panel into the frame.

> ![title](photos/KickAssembly/IMG_7423.jpg)

Bend the leads of the IR sensor so the leads sit flat against the side of the frame.

> ![title](photos/KickAssembly/IMG_7425.jpg)

When the leads are in position, tighten all four screws

> ![title](photos/KickAssembly/IMG_7426.jpg)

Fold the tabs of the frame down to hold everything together

> ![title](photos/KickAssembly/IMG_7427.jpg)

If you want to hang the frame on the wall, use the included rubber bumpers on the four corners of the frame to leave space for the power cable and connectors, and set the frame evenly against the wall.

### Remote Control

Pull the plastic tab at the bottom of the remote to connect the battery

> ![title](photos/KickAssembly/IMG_7430.jpg)

## SmartMatrix Setup

The board comes preprogrammed with the Aurora software and a selection of GIFs we have permission to include.  

Plug in the power supply and you can start using SmartMatrix with the remote control.

### Loading Content

To customize content on SmartMatrix, connect the USB cable to your computer.  Use the remote to navigate to the Settings menu, then "Update Files".  The screen will go blank and SmartMatrix will go into a mode where it looks like a flash drive to the computer.

You can put GIFs into the `/gifs` folder on the SD card.  Edit the `messages.txt` file with a text editor and customize with your own messages, one message per line.

When finished loading content onto SmartMatrix, eject the drive from your computer.  If you don't see anything on the SmartMatrix display, you will need to disconnect the USB cable at least briefly to force USB to disconnect (this is seen on the Mac at least).

### Setting Time

In the Settings menu, there is a menu entry for "Set Time" and "Set Date".  Once you set the date and time it is saved by a battery backup, and the time will keep counting even if you disconnect the power supply.

### Calibrating Audio

Audio Calibration is used to remove noise from the Audio Patterns so you just see your music and not noise in the pattern.  Run calibration without any music playing.  You can connect up your audio source with music pause for the best calibration.  You can run calibration at any time.

In the Settings menu, there is a menu entry for "Audio Calibration".  Inside the settings page, use left/right to choose "Auto", and press select to start calibration.  Press select again to stop, and back to exit the menu.


## Using SmartMatrix

The [Aurora Software Wiki](https://github.com/pixelmatix/aurora/wiki) has some instructions.  We will be adding more later.  Please check back here or in the [SmartMatrix Community](http://community.pixelmatix.com/) for updates, and post any questions you have.

## Modifying SmartMatrix

We will be adding more details.  Please check back here or in the [SmartMatrix](http://community.pixelmatix.com/) Community for updates, and post any questions you have.



