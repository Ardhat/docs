---
title: LEDs
prev: power
current: leds
next: io
published: true
---


{{<ardhat>}} supports LEDs in two ways; the first is through onboard LEDs.

The orange on-board **User LED** on the side opposite the 40-pin header is connected to port D9 of the Ardhat processor, and can be programmed using an Arduino  Sketch in the usual way.

<div class="note info">
  <p>Note that this is different from the standard Arduino port, which is D13. This was done to avoid conflict with the use of D13 for SPI_SCK, and also to allow hardware PWM function can be used, for example for pulsating the LED in sleep mode.</p>
</div>


By way of example, the default factory program, which is available [here](https://github.com/Ardhat/ArdhatFirmata), uses hardware PWM to pulse the User LED when the Pi power is switched off. Pressing the Nav switch toggles  the LED to full, and enables power to the Host.

The other onboard LEDs indicate charge state; Red means charging or running on battery, Green means charged.

The other form of LED support is through the inclusion of a 3.3V to 5V converter on the output of the Pi PWM pin, which can be used to connect WS8212 LED strings directly to Ardhat.

The 5V rail can provide up to 2.5A which is sufficient to drive 4m light strings in normal use (ie not all illuminated at full brightness)

See [Spiralled](https://github.com/Ardhat/spiralLED) for an example of this in use.

<img align="center" src="/media/SpiralLED.jpg">
