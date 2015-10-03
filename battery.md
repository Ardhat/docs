---
title: Battery Operation
prev: io
current: battery
next: expansion
---

 ![image alt text](/media/ardhatbattside400.jpg)


 {{<ardhat>}} can use an optional single cell LiPo battery, and a custom 2200mAh battery that fits snugly between the shield headers is available in the [store](/shop)

<div class="note warning">
  <p>
Any cell with a standard JST-PH connector that physically fits your application may also be used, but make sure the polarity is correct before attachment.
  </p>
</div>


### Battery Operation

During battery operation, {{<ardhat>}} generates the supplies required for the Raspberry Pi and {{<ardhat>}} peripherals from a boost converter. When the remaining battery capacity reaches 5%, the Raspberry Pi is gracefully shutdown (see below) by a power  management daemon, which is also able to schedule events, for example time-lapse image capture.  When the battery voltage reaches a critical level, all circuits are switched off to avoid damage to the battery due to over-discharging. 

### Charge Control System

When connected to external power, the battery is charged using a constant-current /constant-voltage charge algorithm, with pre-conditioning and charge termination phases.

{{<ardhat>}} will charge and maintain any single 3.7V LiPo cell attached to the industry standard 2-pin JST-PH connector.  


If external power is disconnected, Ardhat transitions seamlessly to battery operation, and sends a notification to the Raspberry Pi over the inter-processor communication channel. 