# SmartMatrix Library

## Library Overview
The SmartMatrix Library is designed to make it easy to display graphics and scrolling text on an RGB 16x32 or 32x32 display.  The library stores a buffer and convenient graphics functions to draw to the buffer, with double buffering to update the drawing in a clean manner.  The library supports scrolling text above the graphics layer, and takes care of updating the scrolling text in the background without modifying the drawing buffer.  The library uses the DMA module in the Teensy 3 to refresh the display at a high frame rate and high color-depth with minimal CPU usage.  When CPU is required to refresh the display, it is run in the background as a low-priority interrupt.

**This documentation was based on SmartMatrix Library version 2.x, and is now out of date**  
Version 3.0 has a significantly different API, so many examples here can't be used directly.  [MIGRATION.md](https://github.com/pixelmatix/SmartMatrix/blob/master/MIGRATION.md) describes the differences between version 2.x and 3.0, and how to update a sketch that uses SmartMatrix Library 2.x to work with 3.0.  Version 4.0 is similar to 3.0, and the differences are also described in [MIGRATION.md](https://github.com/pixelmatix/SmartMatrix/blob/master/MIGRATION.md), and there are more details in the [SmartMatrix Library Wiki](https://github.com/pixelmatix/SmartMatrix/wiki).

## How to Use the Library

### Init

*See the README hosted in the [SmartMatrix GitHub Repo](https://github.com/pixelmatix/SmartMatrix/) for installation instructions*

Before using the library, include the appropriate header file for the size of your panel, and the SmartMatrix object to your sketch.  Right now two sizes are supported: 32x32 and 16x32.

```
// for a 32x32 panel
#include <SmartMatrix_32x32.h>
SmartMatrix matrix;
```

```
// for a 16x32 panel
#include <SmartMatrix_16x32.h>
SmartMatrix matrix;
```

Then, initialize the library inside `setup()`:
```
void setup() {
  matrix.begin()
}
```

### Simple Drawing
The library is capable of driving displays with 24-bit color, so color data is stored in a rgb24 object, with 8-bits for each color:
```
typedef struct rgb24 {
  uint8_t red;
  uint8_t green;
  uint8_t blue;
} rgb24;
```

You can define a color that you may use repeatedly during drawing like this:

```
rgb24 myColor = {0xff, 0xff, 0xff}; // white
```

Or set primary colors directly:

```
rgb24 myColor;
myColor.red = 0xff;
myColor.green = 0;
myColor.blue = 0;
```

All drawing functions take an `rgb24` color as an argument.  You can reference a color you set previously, or define the color as part of the function call.
```
rgb24 myColor = {0xff, 0xff, 0xff}; // white
drawPixel(0,0,myColor);
```
```
drawPixel(0,0, {0xff, 0, 0});
```

Drawing functions update a virtual screen that is not used for refreshing the display until the `swapBuffers()` method is called.  The `swapBuffers()` method waits until the next full screen refresh, then swaps the drawing buffer with the refresh buffer to display on the new graphics on the screen.
```
matrix.swapBuffers();
```

By default, `swapBuffers()` makes a copy of the drawing buffer so you can continue adding to your drawing.  If you don't care what's in the drawing buffer because you fill it completely each frame, you can call `matrix.swapBuffers(false)`, which disables the copy and returns faster.

```
matrix.fillScreen({0xff,0,0});
matrix.swapBuffers(false);
delay(1000);
matrix.fillScreen({0,0xff,0});
matrix.swapBuffers(false);
```

The SmartMatrix drawing functions are very similar to the functions used by the Adafruit Graphics Library, with a few differences explained below.  Adafruit has an excellent reference on library functions that mostly applies to the SmartMatrix Library:  
[Adafruit Graphics Library - Adafruit Learning System](http://learn.adafruit.com/adafruit-gfx-graphics-library/graphics-primitives)

SmartMatrix Library differences from Adafruit Graphics Library:

- Color is set using type `rgb24` not `uint16_t`
- Additional functions are available for filled shapes with an outline around the shape
- Multiple font size options are available for drawing characters and scrolling text
- Scaling the fonts is not available as it is better to use a large size font directly
- Not yet implemented: Advanced character drawing functions using `print()`

### Drawing Raw Bitmaps
Here's how to add a bitmap to your Arduino project and display it.

Start by finding a bitmap file that you want to import.  A 32x32 icon is a good place to start, or search Google Images limiting the search to a file sized exactly 32x32 pixels:  
[Google Image Search for "Icon"](https://www.google.com/search?q=icon&tbm=isch&tbs=isz:ex%2Ciszw:32%2Ciszh:32&imgdii=_)

The bitmaps can be smaller than 32x32, but not larger.

Download [GIMP](http://www.gimp.org/downloads/) (GNU Image Manipulation Program), which is a free cross-platform image editing tool.

Open the image in GIMP, make any edits that you want, then under the File menu choose export, and select file type "C Source Code".

Type in a name with .c extension, and click Export.  In the options dialog, first give your bitmap a unique name for "Prefixed Name", this is how you will refer to the image in Arduino.  For this example we'll use "testbitmap".  Uncheck the rest of the options, and make sure Opacity is left at 100.  Click Export.

> ![Image Export](photos/Library/GIMPExport.png)

Copy the .c file to your Arduino project directory.  Include the .c file you created at the top of your project, e.g. `#include "testbitmap.c"`

The `Bitmaps` example included with the SmartMatrix Library gives example code and more details on how to get the bitmap from the C file to the screen.

### Scrolling Text Overview
It's popular to use LED matrix displays for a scrolling text marquee, and the SmartMatrix Library makes this easy to do.  Just configure how you want the text to be displayed, then call `scrollText()` with the text to display and the number of times you want it to scroll across the screen.  The text scrolls on top of the main drawing buffer without modifying it, so you can continue drawing to the screen behind the text.

```
    matrix.setScrollMode(wrapForward);
    matrix.setScrollSpeed(10);
    matrix.setScrollFont(font3x5);
    matrix.setScrollColor({0xff,0xff,0xff});
    matrix.scrollText("Wrap message 4 times", 4);
```
```
    matrix.setScrollMode(bounceForward);
    matrix.setScrollSpeed(20);
    matrix.setFont(font5x7);
    matrix.setScrollColor({0x00,0xff,0x00});
    matrix.scrollText("Bounce Forever", -1);
```

Check the status of your scrolling text by using `getScrollStatus()`, which returns a positive number indicating the number of loops left if running, -1 indicating the scrolling will run forever, or zero indicating scrolling is complete.

```
    matrix.scrollText("Display this message twice", 2);
    
    // wait for scrolling to finish
    while(matrix.scrollText());
    
    matrix.scrollText("Then display this message once", 1);
```

You can stop the scrolling text at any time by using `stopScrollText()`.

```
    matrix.scrollText("Scroll this text forever", -1);

    delay(1000);
    matrix.stopScrollText();
```

### Configuration Overview
There are several options that can be configured in the library.

**Rotation**  
To rotate the display in a multiple of 90 degrees, use `setRotation(rotationDegrees rotation)`;

```
matrix.setRotation(rotation180);
```
It's best to do this early before drawing anything to the display.  Data drawn to the buffer is not rotated, so if you need to rotate in the middle of your program, do this:

```
matrix.fillScreen({0,0,0}); // clear screen by filling with black
matrix.swapBuffers();
matrix.setRotation(rotation90); // rotate to 90 degree position
// now draw your screen again
```

After rotating the screen, the width and height of the buffer may change.  You can get quick access to the current width and height with these functions:
```
uint16_t getScreenWidth(void);
uint16_t getScreenHeight(void);
```

For example draw a white border around the screen (this example works with all rotations - even on non-square 16x32 display)
```
matrix.drawRectangle(0,0, matrix.getScreenHeight()-1, matrix.getScreenWidth()-1, {0xff, 0xff, 0xff});
```

LED displays can be very bright, and sometimes you want to dim the display.  The SmartMatrix Library makes this easy without losing color-depth while dimming
```
void setBrightness(uint8_t brightness);

matrix.setBrightness(255); // max brightness
matrix.setBrightness(25); // 10% brightness, for a dark room
```

**Color Correction**

TBD color correction explanation

There is an option to enable and disable color correction:

```
void setColorCorrection(colorCorrectionModes mode);
```
```
e.g.
rgb24 fullRed = {0xff, 0, 0};
rgb24 halfRed = {0xff/2, 0, 0};
rgb24 quarterRed = {0xff/4, 0, 0};

matrix.setColorCorrection(ccNone);
matrix.drawRectangle(0,0, matrix.getScreenHeight(), matrix.getScreenWidth()/3, fullRed);
matrix.drawRectangle(matrix.getScreenWidth()/3,0, matrix.getScreenHeight(), matrix.getScreenWidth()/3, halfRed);
matrix.drawRectangle(matrix.getScreenWidth()/3*2,0, matrix.getScreenHeight(), matrix.getScreenWidth()/3, quarterRed);
matrix.swapBuffers();
```

The red rectangle on the left is twice as bright as the one in the middle, and four times as bright as the one on the right, but it doesn't look that way to our eyes.

Add this to the code to try it again with color correction enabled:
```
matrix.setColorCorrection(cc24);
```

## Library Files
### Main Header - SmartMatrix.h
This header holds the SmartMatrix class definition, and various structs and enums needed for the user to interact with the SmartMatrix library.

The hardware-specific `MatrixHardware_*.h` file is included here.  To select a different hardware configuration for the library, change the `#include "MatrixHardware_*.h` to the file that describes your hardware.

### Fonts
Fonts are stored as bitmaps that are linked to the firmware.  To make a new font, start with an existing font in [BDF format](http://en.wikipedia.org/wiki/Glyph_Bitmap_Distribution_Format).  The fonts that come with the SmartMatrix library were sourced from Apple's [public domain fonts](http://www.opensource.apple.com/source/X11fonts/X11fonts-14/font-misc-misc/font-misc-misc-1.1.2/).  To convert to a C source file, use the [bdf2c](http://sourceforge.net/projects/bdf2c/) utility.

MatrixFont.cpp provides methods for looking up individual characters in a bitmap font.

TODO: add full instructions on converting the font, and the manual .c file manipulation needed to include the font bitmap file in the library.

### Hardware Specific
All hardware-specific code and definitions are kept in two files: SmartMatrix.cpp and MatrixHardware_*.h.

SmartMatrix.cpp is specific to the Freescale Kinetis MK20DX microcontroller used in the Teensy 3.0 and 3.1.  The code takes care of initializing the hardware, updating display data buffers in the background, and setting up DMA to move the data to the display.  The code is written to be flexible to slight variations in hardware, which are set in the MatrixHardware_*.h header file.

Only one of the the MatrixHardware_*.h files should be included by the project.  Each header holds definitions that may change depending on the size and configuration of the display that is attached to the microcontroller, or may change depending on the pins used to connect the microcontroller to the display.  There are options to change the refresh rate, color depth, and number of rows that are buffered that may be changed to modify the amount of resources (CPU cycles and RAM) required to refresh the display.  If the application affects the DMA module, by using DMA for another purpose or changing the CPU clock for example, there are delays that can be adjusted to compensate.

### Drawing
MatrixBackground.cpp holds the code for drawing to the virtual screen.

### Scrolling Text
MatrixForeground.cpp has the code that implements the scrolling text layer.

### Color
MatrixColor.cpp holds the code to work with rgb24 values, and the code and lookup tables to do color conversion.

### Configuration
MatrixConfig.cpp provides methods for setting options like screen rotation and brightness.
