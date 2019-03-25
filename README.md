# ServoEasing - move your servo more natural
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Build Status](https://travis-ci.org/ArminJo/ServoEasing.svg?branch=master)](https://travis-ci.org/ArminJo/ServoEasing)

Youtube video of ServoEasing in action

[![Demonstration of different servo easings](https://i.ytimg.com/vi/fC9uxdOBhfA/hqdefault.jpg)](https://www.youtube.com/watch?v=fC9uxdOBhfA)

## Servo easing library for Arduino
This is a library for smooth servo movements. It can be used directly with a [PCA9685 servo expander](https://learn.adafruit.com/16-channel-pwm-servo-driver?view=all) or the Arduino Servo Library or the included Lightweight Servo library.
The latter is useful, if you have only one or two servos since it uses only the internal timer with no software overhead.

- **Linear** as well as other ease movements for all servos attached to the Arduino Servo library are provided.
- All servos can move **synchronized**.
- It enables **non blocking** movement for all servos attached to the Arduino Servo library by reusing the interrupts of the servo timer.

### Includes the following **easing functions**:
- Linear
- Quadratic
- Cubic
- Quartic
- Sine
- Circular
- Back
- Elastic
- Bounce
- User defined

### All easing functions can be used in the following **variants**:
- In
- Out
- InOut
- BouncingOutIn (mirrored Out) -> BouncingOutIn of the Sine function results in the upper half of the sine.

## Useful resources
- [Easings Cheat Sheet](https://easings.net/)
- [Robert Penner](http://www.robertpenner.com/easing/)
- [C functions on Github](https://github.com/warrenm/AHEasing/blob/master/AHEasing/easing.c)
- [Interactive cubic-bezier](http://cubic-bezier.com)

## Using PCA9685 16-Channel Servo Expander
To enable it, use `Sketch/Show Sketch Folder (Ctrl+K)` in the Arduino IDE, navigate to the `src` folder, open ServoEasing.h and comment out line 32 or define global symbol `USE_PCA9685_SERVO_EXPANDER` which is yet not possible in Arduini IDE:-(.

## Using the included Lightweight Servo library
Using the **Lightweight Servo Library** reduces sketch size and makes the servo pulse generating immune to other libraries blocking interrupts for a longer time like SoftwareSerial, Adafruit_NeoPixel and DmxSimple.<br/>
To enable it, use `Sketch/Show Sketch Folder (Ctrl+K)` in the Arduino IDE, navigate to the `src` folder, open ServoEasing.h and comment out line 43 or define global symbol `USE_LEIGHTWEIGHT_SERVO_LIB` which is yet not possible in Arduini IDE:-(.<br/>
If not using the Arduino IDE take care that Arduino Servo library sources are not compiled / included in the project.

## Reducing library size
If you have only one or two servos, then you can save program space by using Lightweight Servo library .
This saves 742 bytes FLASH and 42 bytes RAM.<br/>
If you do not need the more complex easing functions like `Sine` etc., which in turn need sin(), cos(), sqrt() and pow(), you can shrink library size by approximately 2100 bytes by defining the symbol KEEP_LIBRARY_SMALL or comment out line 34 in ServoEasing.h.
 
## SymmetricEasing example
This example shows symmetric (end movement is mirror of start movement) linear, quadratic and cubic movements for 3 servos synchronously.

## AsymmetricEasing example
This example shows asymmetric (end movement is different from start movement) partially **user defined** (line 140) non linear movements for 3 servos synchronously.

## EndPositionsTest example
This example helps you determine the right end values for your servo.<br/>
These values are needed for the `attach()` function, if your servo does not comply to the standard values. 
E.g. some of my SG90 servos have a 0 degree period of 620 �s instead of the standard 544.<br/>
This example does not use the ServoEasing functions.

## SpeedTest example
This example gives you a feeling how fast your servo can move.<br/>This example does not use the ServoEasing functions.

## Travis CI
The ServoEasing library examples are built on Travis CI for the following boards:

- Arduino Uno
- Arduino Leonardo
- Arduino cplayClassic
- Arduino Mega 2560

## Requests for modifications / extensions
Please write me a PM including your motivation/problem if you need a modification or an extension e.g. a callback functionality after move has finished.