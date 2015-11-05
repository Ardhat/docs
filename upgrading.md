---
title: Upgrading
prev: progmodel
current: upgrading
next: sleep
published: true
---


Before using Ardhat, make sure you have upgraded to the latest supported version of your host operating system and apps.

If using Ardhat on a Raspberry Pi, see [this guide](https://www.raspberrypi.org/documentation/raspbian/updating.md) on the foundation website.

## Updating the bootloader

The bootloader used in {{<ardhat>}} is a modified verion of Optiboot, and is loaded at the factory together with a default Sketch that runs Firmata and also manages the Navigation switch and LED.

If required, this bootloader and app can be replaced using the following procedure:

1. Download the ArdhatCloner Sketch from [here](https://github.com/Ardhat/ArdhatCloner)
2. Using the instructions provided in the Sketch, connect an Arduino or compatible processor to the Ardhat ICSP (you can use some simple jumpers as hown in the image below)

<img align="center" src="/media/ArdhatProg.jpg">


3. Install the ArdhatCloner sketch on the Arduino.
4. Restart the Arduino, and the ArdhatCloner sketch will install the latest bootloader and factory default app

If you want to load a custom app in place of the factory app, use JC wipplers hex2c.tcl to create the data.h file that ArdhatCloner uses.



