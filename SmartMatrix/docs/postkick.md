# SmartMatrix Display

**SmartMatrix is now a retired product**

It's possible to make your own SmartMatrix Display using a SmartLED Shield, Teensy, and [free instructions](http://www.instructables.com/id/SmartMatrix-Dynamic-LED-Art-Display/).

## What is SmartMatrix?

SmartMatrix is a beautiful music visualizer, dynamic art display, video game art display, and more. It's controllable, customizable, and extendable, allowing you to display your own animations and messages.

> <iframe src="https://player.vimeo.com/video/128016189" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

Customize what's on the screen with the included remote control: choose what's playing, show a clock or message on top, and change settings, all from the remote. You don't need a computer or phone to control what's on the screen.

> <iframe src="https://vine.co/v/eih2bxetUpH/embed/simple" width="480" height="480" frameborder="0"></iframe><script src="https://platform.vine.co/static/scripts/embed.js"></script>

Patterns are generated on the fly by SmartMatrix and can be customized by selecting a color palette to match your decor or mood.  SmartMatrix includes 36 patterns as of June 2015, and more are added with each new software release.

> <iframe src="https://player.vimeo.com/video/127417451" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

Audio patterns react to music connected via a headphone-style cable. Cycle through the included patterns along with your favorite color palette. Connect SmartMatrix to the line-out port of your stereo or sound card, or use the included Y-adapter to tap into the signal between your audio source and speakers.

> <iframe src="https://player.vimeo.com/video/127414667" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

Play 32x32 pixel GIF Animations on SmartMatrix. Find, convert or create your own 32x32 pixel GIF with any software that outputs GIF files and drag it to the SmartMatrix USB drive to add new animations.

> ![SmartMatrix](photos/SmartMatrixDisplay/gifonwall.gif)

It's quite easy to use free online tools to convert large videos and GIFs into 32x32 pixel size, and we're sharing a growing collection <a href="http://community.pixelmatix.com/t/animated-gif-collection/26" target="_blank">in our forums</a>.

> <iframe src="https://player.vimeo.com/video/129597324" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

On top of any content (Patterns, Audio Patterns, Animations), you can display a clock or scrolling message. A built in Real Time Clock module keeps track of the time, with battery backup to keep time even when unplugged.

### Why LEDs?

The LED matrix gives a unique look that can't be reproduced by a computer monitor or TV. The individual LEDs are bright enough to be seen across a room in daylight but can also be dimmed to not be distracting at night. SmartMatrix uses unique technology to show excellent color contrast and depth and a fast refresh rate to get rid of distracting flicker.

## What do we get?

We're packaging SmartMatrix as an easy to assemble kit, requiring just a screwdriver and a few minutes to put together. If you don't want to assemble the kit yourself, we have an assembled version that is ready to go out of the box.

> <iframe src="https://player.vimeo.com/video/129599847" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

The kit comes with everything needed for SmartMatrix to run on its own. You only need to connect to a computer to load new GIFs or messages, and you can connect the included audio cables to your audio source for music visualization.  
  
> ![SmartMatrix Kit Contents](photos/SmartMatrixDisplay/kitcontents.jpg)  
  
* 32x32 pixel RGB LED matrix panel  
* SmartMatrix circuit board with clock battery backup and 4GB microSD Card  
* Power adapter, USB cable, headphone-size (1/8") audio cable with Y-adapter
* 9"x9" shadowbox picture frame customized with laser cut panel in the back, and specialty lighting acrylic in the front
* Remote control, receiver, and cable
* Miscellaneous small parts for assembly


## Our Story

SmartMatrix started as a DIY kit for electronics enthusiasts to connect an Arduino-like Development Board to LED panels. We released the kit and code to drive the display as open source at Maker Faire in May 2014 and got a lot of interest from people that wanted to build their own products with an LED display. Adafruit Industries carries <a href="https://www.adafruit.com/products/1902" target="_blank">our kit</a> and has sold over 500 in the last year.

> ![SmartMatrix Shield](photos/Shop/AdafruitSmartMatrixKit.jpg)
Photo courtesy Adafruit

At Maker Faire we met a lot of people that were interested in the display but had never soldered or didn't have the time or skills to program an application for SmartMatrix. Four months later at World Maker Faire in New York City we released the SmartMatrix Bundle - the precursor to SmartMatrix - that included pre-made software for playing patterns and animations with a remote control interface. The bundle was popular but many interested visitors to our booth were disappointed to find it required about 30 minutes of soldering to assemble.

> ![Maker Faire](photos/SmartMatrixDisplay/makerfaire.jpg)

SmartMatrix is a continuation of the project - making it accessible to more people by manufacturing a custom board with all the parts soldered. Now assembling the kit only takes a few minutes without any special skills or tools. We added a few new features including music visualization, the Real Time Clock module, and a custom remote.

> ![SmartMatrix Progression](photos/SmartMatrixDisplay/progression.jpg)

### SmartMatrix and Open Source

SmartMatrix started as an Open Source project and continues to be. You can find [hardware](https://github.com/pixelmatix/SmartMatrix/tree/master/hardware) and [software](https://github.com/pixelmatix/aurora) details in our GitHub repos, and a tutorial on how to put together a SmartMatrix display using development boards and a bit of through-hole soldering on [Instructables](http://www.instructables.com/id/SmartMatrix-Dynamic-LED-Art-Display/).

> ![SmartMatrix Hacking](photos/SmartMatrixDisplay/hacking.jpg)

The main software on SmartMatrix is an open source Arduino sketch called Aurora that can run on a Teensy 3.1 as well as the custom SmartMatrix board. We include instructions on how to compile all of the software yourself using free tools.  We brought power, programming, serial, and I2C signals out to pads on the board if you want to extend the functionality of your SmartMatrix.

## Acknowledgements

SmartMatrix wouldn't be possible without a lot of open source code, tools, and information shared by others.

* Paul Stoffregen ([PJRC](http://pjrc.com/)) - The [Teensy 3.1](http://pjrc.com/teensy/index.html) and [Teensyduino](http://pjrc.com/teensy/teensyduino.html) Arduino add-on made an excellent development platform for building SmartMatrix, and the idea for the SmartMatrix Library was conceived while reading [an article](https://www.pjrc.com/teensy/td_libs_OctoWS2811.html) about Paul's OctoWS2811 Library
* Micah Elizabeth Scott - [Fadecandy](http://scanlime.org/2013/11/fadecandy-easier-tastier-and-more-creative-led-art/) was another source for inspiration while building SmartMatrix. The SmartMatrix board borrows a few ideas from Fadecandy like the Hacker Port for programming, and the SmartMatrix Library has a few snippets of Fadecandy code
* Craig Lindley - Playing GIFs natively on SmartMatrix is made possible by Craig's [open source GIF decoder](https://github.com/pixelmatix/animatedgifs/), and Craig's [Light Appliance](http://www.craigandheather.net/celelightappliance.html) project was the idea for turning SmartMatrix into an untethered product with a remote control
* Daniel Garcia and Mark Kriegsman ([FastLED](http://fastled.io/)) - Nearly all the patterns in SmartMatrix depend on the FastLED library, and many of the patterns are made with open source code from the [FastLED community](http://fastled.io/+)
* [Stefan Petrick](https://plus.google.com/115124694226931502095/posts) - Some of the best looking patterns on SmartMatrix are contributed by Stefan, and his [Funky Clouds](https://www.youtube.com/watch?v=Uc5ZqxDS5ZY) project inspired the Audio Patterns in SmartMatrix
* [Al Linke's Pixel](http://ledpixelart.com/) and [Jeremy Williams' Game Frame](https://www.kickstarter.com/projects/jerware/game-frame-the-art-of-pixels/description) - These previous Kickstarter successes were inspirations for SmartMatrix and the creators were open with sharing their Kickstarter stories to help others
* Chasm Animated GIFs are used with permission from Discord Games, Inc., makers of [Chasm](http://www.chasmgame.com)








# SmartMatrix Details

## SmartMatrix Setup

The board comes preprogrammed with the Aurora software and a selection of GIFs we have permission to include.

If you purchased the "Kit" version, you need to assemble it first, [click here for instructions](#smartmatrix-after-kickstarter-assembling-smartmatrix).

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

The "Kit" version of SmartMatrix comes ready to assemble in minutes, with no soldering required.  See [SmartMatrix Display Assembly](smartmatrix-assembly.html) for instructions.


## Modifying SmartMatrix

If you don't see what you're looking for, please post in the [SmartMatrix Community](http://community.pixelmatix.com/).

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
|:----:|:--------:|:------------:|:------------:|
| TX (out)   | UART1 TX | 31           | E0           |
| RX (in)   | UART1 RX | 26           | E1           |
| SDA  |  I2C SDA | 17           | B1           |
| SCL  |  I2C SCL | 16           | B0           |

VUSB is slightly less than 5V - it's a diode OR of external power and USB power.  
3.3V is drawing from the Kinetis 3.3V output, limited to 100mA

[hackerport]:https://github.com/scanlime/fadecandy
[teensy31]:https://www.pjrc.com/teensy/index.html
[smartmatrixshield]:docs.pixelmatix.com/SmartMatrix/shieldref.html

