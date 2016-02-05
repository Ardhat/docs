---
category: Getting Started
title: Configuration
prev: overview
current: configuration
next: quickstart
published: true
---

#### Protecting shield pins

<div class="note warning">
  <p>Before fitting {{<ardhat>}} to a Raspberry Pi, be sure that you either fit spacers between the boards or place the insulating foam supplied on the Pi HDMI connector to prevent short-circuits on the shield connector which may cause damage to {{<ardhat>}}</p>
</div>


#### Arduino shield headers

Some versions of {{<ardhat>}} do not come with headers pre installed, which gives you the option of running as a pure lightweight HAT, or as an Arduino compatible module. If you want to populate the supplied Arduino headers, a good trick to make sure you get them straight is to fit a shield to the headers _before_ soldering. Use a fine tipped iron and fine core solder (1mm).


#### Writing to HAT eeprom

By default on the {{<ardhat>}} this is enabled. To disable remove the solder jumper bridge from the CFG jumper next to the RTC output pin.


#### Radio antenna

If you have a radio equipped {{<ardhat>}}, you'll need to attach an antenna to the board. 

<div class="note warning">
  <p>Do not load the radio driver without an antenna attached, as running the transmitter without an appropriate load could cause permanent damage to the radio module</p>
</div>

The attach point is near the radio module, and is marked with an antenna symbol on the top side of the board. The antenna is best left straight but will also work coiled but with a small effect on RSS (Received Signal Strength). The length of wire needed depends on the radio module frequency you have selected, and {{<ardhat>}} is supplied with a 1/4 wave antenna of appropriate length. For reference, the required antenna lengths are:

**433MHz:**

- 1/4 wave = 164.7mm
- 1/2 wave = 329.4mm
- full wave = 692.7mm

**868MHz:**

- 1/4 wave = 82.2mm
- 1/2 wave = 164.3mm
- full wave = 345.5mm

**915MHz:**

- 1/4 wave = 77.9mm
- 1/2 wave = 155.9mm
- full wave = 327.8mm
