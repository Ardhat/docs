---
title: Power
weight: 30
toc: true
prev: configuration
current: power
next: leds
---



{{<ardhat>}} supports external power from a 2.1mm DC power jack, which is the same as is used by Arduinos and many laptop power supplies.

The wide input voltage range mean that just about any laptop power supply that physically fits can be used.

Adapters are available to connect to bare wires,for example to use in cars and R<img align="right" style="width:200px;height:200px" src="/media/005AX.jpg">Vs.


This input is protected against polarity reversals and over-current and will accept any voltage from 8-28V. The polarity protected voltage from this connector is presented to the Arduino shield header for use by shields. {{<ardhat>}} integrates a 5v@ 3A switching regulator driven by this external supply , for use by peripherals, such as small servo motors or ESCs. Note that the maximum current drawn by shields from the 5V rail must be less than 2.5A.  


5V power to the Raspberry Pi is switched off by setting {{<ardhat>}} pin A3 high, which drives a power MOSFET to turn off 5V power to Raspberry Pi, or compatible.

<div class="note">
  <p>Note that the Raspberry Pi will not turn off if it is connected to USB power on its micro-USB connector.
Also note that power from the Raspberry Pi will always be supplied to Ardhat even if this switch is off.</p>
</div>


{{<ardhat>}} also support solar charging using the 0.1" header next to the ICSP header.

<div class="note warning">
  <h5>NB {{<ardhat>}} requires a 6V solar panel</h5>
  <p>Also please ensure the polarity is correct, as this input is not protected against polarity reversal. Ground is the pin nearest the edge of the board</p>
</div>
