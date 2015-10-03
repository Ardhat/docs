---
title: Mesh Radio
prev: env
current: radio
next: contributing
---


 ![image alt text](/media/ardhatradio400.jpg)


### Long-range wireless node

{{<ardhat>}} includes an optional long-range wireless mesh network transceiver that operates on either 433, 868, or 915 MHz  license-free ISM (Industrial, Scientific and Medical) frequency bands. Using lower frequencies than those of the 2.4 or 5.8 GHz ISM bands enables much better coverage to be achieved especially when the nodes are within buildings. 

{{<ardhat>}} is available with 2 radio transceiver options. The first is compatible with the Moteino and [EmonCMS](http://emoncms.org/) nodes and can thus enable the Raspberry Pi as a gateway or master controller.  The second uses the LoRa RF physical layer, a form of spread spectrum modulation that significantly increases the link budget. 

With both options, the radio nodes are driven by the Arduino processor, so they can be maintained at very lower power, only waking up the Raspberry Pi when required.