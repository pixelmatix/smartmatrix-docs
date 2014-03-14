# SmartMatrix Library

## Library Overview
The SmartMatrix Library is designed to make it easy to display graphics and scrolling text on an RGB 16x32 or 32x32 display.  The library stores a buffer and convenient graphics functions to draw to the buffer, with double buffering to update the drawing in a clean manner.  Scrolling text can be displayed above the graphics layer, and the library takes care of moving the scrolling text in the background.  The library uses the DMA module in the Teensy 3 to refresh the display at a high frame rate and high color-depth with minimal CPU usage.  When CPU is required to refresh the display, it is done in the background as a low-priority interrupt.


## Overview of interaction

### Init

Before using the library, add a SmartMatrix object to your sketch:
```
SmartMatrix matrix;
```

Initialize the library:
```
matrix.begin()
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

Drawing functions update a virtual screen that is not used for refreshing the display until the `swapBuffer()` method is called.  The `swapBuffer()` method waits until the next full screen refresh, then swaps the temporary drawing buffer with the refresh buffer.
```
matrix.swapBuffer();
```

The SmartMatrix drawing functions are very similar to the functions used by the Adafruit Graphics Library, with a few differences explained below.  Adafruit has an excellent reference on library functions that mostly applies to the SmartMatrix Library:  
[Adafruit Graphics Library - Adafruit Learning System](http://learn.adafruit.com/adafruit-gfx-graphics-library/graphics-primitives)

**SmartMatrix Library differences from Adafruit Graphics Library**

- Color is set using type `rgb24` not `uint16_t`
- TODO: Check order of arguments

TODO: Now that we know how to draw to the screen, let's do a simple drawing:
- Added additional functions for filled shapes that draws an outline around the shape
- Added multiple font size options for drawing characters and scrolling text
- Scaling the fonts is not available as it is better to use a large size font directly
- Not yet implemented: Advanced character drawing functions using `print()`

Don't forget the matrix.swapBuffer() call at the end

### Scrolling Text
It's popular to use these displays for a scrolling text marquee, and the SmartMatrix Library makes it easy to add this to your display.  Just configure how you want the text to be displayed, then call `scrollText()` with the text to display and the number of times you want it to scroll across the screen.  The text scrolls on top of the main drawing buffer without modifying it, so you can continue drawing to the screen behind the text.

```
    matrix.setScrollMode(SCROLLMODE_WRAP);
    matrix.setScrollSpeed(10);
    matrix.setFont(font3x5);
    matrix.setScrollColor({0xff,0xff,0xff});
    matrix.scrollText("Wrap message 4 times", 4);
```
```
    matrix.setScrollMode(SCROLLMODE_BOUNCE_FORWARD);
    matrix.setScrollSpeed(20);
    matrix.setFont(font5x7);
    matrix.setScrollColor({0x00,0xff,0x00});
    matrix.scrollText("Bounce Forever", -1);
```

### Configuration
There are several options that can be configured in the library.

**Rotation**  
To rotate the display in a multiple of 90 degrees, use `setRotation(rotationDegrees rotation)`;

```
matrix.setRotation(rotation180);
```
It's best to do this early before drawing anything to the display.  Data drawn to the buffer is not rotated, so if you need to rotate in the middle of your program, do this:

```
matrix.fillScreen({0,0,0,}); // fill with black
matrix.swapBuffer();
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

In order to do color correction within the 24-bit color capable with this hardware, applying color correction will limit the color range. (e.g. adding or subtracting a small value to a color's brightness may have no effect on the brightness of the LED.)  There is an option to enable and disable color correction:

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
matrix.swapBuffer();
```

The red rectangle on the left is twice as bright as the one in the middle, and four times as bright as the one on the right, but it doesn't look that way to our eyes.

Add this to the code to try it again with color correction enabled:
```
matrix.setColorCorrection(cc24);
matrix.swapBuffer();
```

TODO: swapBuffer with no arguments does copy

### Interrupt Details
The low-priority interrupt...
calculations to get CPU usage


## Functions

### Initialization
SmartMatrix();
void init();

### Drawing Functions

### Scrolling Text

### Configuration

## Library Files
### Main Header - SmartMatrix.h

### Fonts - move to folder?

### Hardware Specific
All hardware-specific code and definitions are kept in two files: SmartMatrix.cpp and MatrixHardware.h

SmartMatrix.c is specific to the Freescale Kinetis MK20DX microcontroller used in the Teensy 3.0 and 3.1.  The code takes care of initializing the hardware, updating display data buffers in the background, and setting up DMA to move the data to the display.

SmartMatrix.h holds definitions that may change depending on the size and configuration of the display that is attached to the microcontroller, or may change depending on the pins used to connect the microcontroller to the display.  There are options to change the refresh rate, color depth, and number of rows that are buffered that may be changed to modify the amount of resources (CPU cycles and RAM) required to refresh the display.  If the application affects the DMA module, by using DMA for another purpose or changing the CPU clock for example, there are delays that can be adjusted to compensate.

### Drawing

### Color

### Configuration

### Scrolling Text




