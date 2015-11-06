---
title: LEDs
prev: power
current: leds
next: io
published: true
---


{{<ardhat>}} supports LEDs in two ways; the first is through an onboard LED that is connected to port D9. Note that this is different from the standard Arduino port, which is D13.

This was done to avoid conflict with the use of D13 for SPI_SCK, and also so that the hardware PWM function can be used, for example for pulsating the LED in sleep mode.

The other form of support is through the inclusion of a 3.3V to 5V converter on the output of the Pi PWM pin, which can be used to connect WS8212 LED strings directly to Ardhat.

The 5V rail can provide up to 2.5A which is sufficient to drive 4m light strings in normal use (ie not all illuminated at full brigtness)

See [Spiralled](https://github.com/Ardhat/spiralLED) for an example of this in use.

<img align="center" src="/media/SpiralLED.jpg">
