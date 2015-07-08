# SmartMatrix After Kickstarter
Our Kickstarter campaign ended, but the SmartMatrix project isn't over.  We're selling the SmartMatrix units we already built, with free shipping to the US, while supplies last:

<a href="https://shop.trycelery.com/page/556bb89a502fad0b00edf08d" data-celery="556bb89a502fad0b00edf08d" data-celery-version="v2">Order SmartMatrix Now ></a>
<script async type="text/javascript" src="https://www.trycelery.com/js/celery.js"></script>  

> ![SmartMatrix](photos/KickStaffPick.jpg)

Please join our list to find out when SmartMatrix is available outside the US. We'll extend a discount to non-US customers on the list when we do our wider release:  [SmartMatrix Non-US Waiting List](http://eepurl.com/bnEwKv)

If you know how to solder you can put together a SmartMatrix display yourself.  Check out our [Instructable](www.instructables.com/id/SmartMatrix-Dynamic-LED-Art-Display/), or the [shop page](shop.html) to find out where you can buy the SmartMatrix Shield.

Please join [our mailing list](http://eepurl.com/UX2V5) to get the latest updates on SmartMatrix.  [Join us in the forums](http://community.pixelmatix.com/) if you have any questions or you'd like to have a conversation.


## SmartMatrix Setup

The board comes preprogrammed with the Aurora software and a selection of GIFs we have permission to include.

If you purchased the "Kit" version, you need to assemble it first, [click here for instructions](#assembling-smartmatrix).

If you purchased the "Assembled" version, remove the tape and cardboard used to protect the IR sensor and keep it in place during shipping.  Pull the plastic tab out of the bottom of the remote control to connect the battery.

Plug in the power supply and you can start using SmartMatrix with the remote control.

Aurora boots to a menu that lets you select between Patterns, Audio Patterns, Animations, and Settings.  Press the select button (circle button) on the remote to enter any of these modes.

Select content to play with the left/right buttons.  The Playback button lets you change playback modes to cycle through content sequentially or randomly.  In Patterns and Audio Patterns you can customize the color palette with the Palette button.  The overlay button shows one of the clock faces or messages.

The [Aurora Software Wiki](https://github.com/pixelmatix/aurora/wiki) has more details on Aurora's features.

### Loading Content

To customize content on SmartMatrix, connect the USB cable to your computer.  Use the remote to navigate to the Settings menu, then "Update Files".  The screen will go blank and SmartMatrix will go into a mode where it looks like a flash drive to the computer.

You can put GIFs into the `/gifs` folder on the SD card.  Edit the `messages.txt` file with a text editor and customize with your own messages, one message per line.

When finished loading content onto SmartMatrix, eject the drive from your computer.  If you don't see anything on the SmartMatrix display, you will need to disconnect the USB cable at least briefly to force USB to disconnect (this is necessary on the Mac, and possibly other computers).

### Setting Time

In the Settings menu, there is a menu entry for "Set Time" and "Set Date".  Once you set the date and time it is saved by a battery backup, and the time will keep counting even if you disconnect the power supply.

### Calibrating Audio

Audio Calibration is used to remove noise from the Audio Patterns so you just see your music and not noise in the pattern.  Run calibration without any music playing.  You can connect up your audio source with music paused for the best calibration.  You can run the calibration again at any time.

In the Settings menu, there is a menu entry for "Audio Calibration".  Inside the settings page, use left/right to choose "Auto", and press select to start calibration.  Press select again to stop, and back to exit the menu.


## Assembling SmartMatrix

The "Kit" version of SmartMatrix comes ready to assemble in minutes, with no soldering required.

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

Slide the end of the cable between the plastic frame and the the circuit board on the back side of the LED Matrix panel.  

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



## Modifying SmartMatrix

If you don't see what you're looking for, please post in the [SmartMatrix](http://community.pixelmatix.com/) Community.

### Running custom code on SmartMatrix

SmartMatrix development was done using the [Teensy 3.1][teensy31] and the [SmartMatrix Shield][smartmatrixshield], with code compiled in the Arduino IDE with Teensyduino add-on.  The Teensy 3.1 has a bootloader chip containing special code to connect to a loader application on the computer and transfer new firmware.  SmartMatrix doesn't have the bootloader chip, and instead has a completely different bootloader that takes files in a special format.  

You can compile code for SmartMatrix using the Arduino IDE and Teensyduino add-on, after making a few modifications.

#### Arduino Modifications to compile Aurora or your own code

First, install the latest Arduino IDE and Teensyduino add-on.  Follow the  instructions for compiling Aurora and make sure you can compile Aurora for the Teensy 3.1 board.  
https://github.com/pixelmatix/aurora/wiki/Compiling

Next, download the `srec_cat` tool and modify the Arduino install to create a binary with 0x8080 offset.  The Linker Script option should be set to "0x8080 Offset" to compile a binary that will run on the SmartMatrix Display.
https://github.com/pixelmatix/JumpToAppWithOffset

Finally, either run `srec_cat` from the commandline to generate `software.bin`, or modify the Arduino IDE to give a menu option for running srec_cat after compiling.  
https://github.com/pixelmatix/uTaskerBootWithArduinoApp

#### Loading software.bin onto SmartMatrix
There are two options for loading new firmware.  You can run the bootloader at startup by holding down the button while applying power, or you can load software.bin onto the root of the microSD card where it will overwrite the firmware when the SmartMatrix CPU restarts.

**Failsafe Bootloader**  
This option will always be available, even when there is no microSD card inserted, or there is no firmware installed.

1. Disconnect all power (including USB)
2. Hold button on back of SmartMatrix while connecting USB
3. Look for flashing red light midway up the right side of SmartMatrix, and fast flashing light on back of SmartMatrix
4. Release button
5. Look for `SMARTMATRIX_BOOT` drive on your computer
6. Open drive and delete existing `software.bin` file if present
7. Copy over new `software.bin` file into root of drive
8. Drive will disconnect automatically, ignore any warnings by the OS on improperly connecting drive

**MicroSD Bootloader**  
1. Load `software.bin` onto the root of the microSD card - you can use the "Update Files" option in Aurora
2. Restart SmartMatrix - you can cycle power, or eject the drive and disconnect the USB cable from the computer
3. You should see a fast flashing red light in the upper right corner of SmartMatrix, and a fast flashing yellow light on the back of SmartMatrix.  Don't disconnect power while the light is flashing as it is updating the software
4. When complete, the bootloader will delete `software.bin` from the microSD card
5. Note: If `software.bin` is invalid (it is not the right size and/or the CRC check fails), there will be no flashing red light and the file will not be deleted.

### Connecting to other electronics

The expansion port - based on Fadecandy's [Hacker Port][hackerport] layout - has connections for UART, I2C, and power.  Outputs are at 3.3V but inputs are 5V tolerant.  I2C pull-ups are not installed.  Full hardware details are in the [SmartMatrix GitHub Repo](https://github.com/pixelmatix/SmartMatrix/tree/master/hardware), see the files starting with "SmartMatrix_V1".

| Name | Function | Teensy Pin # | Kinetis GPIO |
-:----:|:--------:|:------------:|:------------:|
| TX (out)   | UART1 TX | 31           | E0           |
| RX (in)   | UART1 RX | 26           | E1           |
| SDA  |  I2C SDA | 17           | B1           |
| SCL  |  I2C SCL | 16           | B0           |

VUSB slightly less than 5V and is a diode OR of external power and USB power.  
3.3V is drawing from the Kinetis 3.3V output, limited to 100mA

[hackerport]:https://github.com/scanlime/fadecandy
[teensy31]:https://www.pjrc.com/teensy/index.html
[smartmatrixshield]:docs.pixelmatix.com/SmartMatrix/shieldref.html

