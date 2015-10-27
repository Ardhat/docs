---
title: Mesh Radio
prev: env
current: radio
next: contributing
published: true
---



 ![image alt text](/media/ardhatradio400.jpg)


### Long-range wireless node

{{<ardhat>}} includes an optional long-range wireless mesh network transceiver that operates on either 433, 868, or 915 MHz  license-free ISM (Industrial, Scientific and Medical) frequency bands. Using lower frequencies than those of the 2.4 or 5.8 GHz ISM bands enables much better coverage to be achieved especially when the nodes are within buildings. 

{{<ardhat>}} is available with 2 radio transceiver options. The first is compatible with the Jeelabs, Moteino and [EmonCMS](http://emoncms.org/) nodes and can thus enable the Raspberry Pi as a gateway or master controller.  Ardhat uses the high power verion of the HopeRF module, the RFM68HCW. 
The second uses the LoRa RF physical layer, a form of spread spectrum modulation that significantly increases the available link budget. 

With both options, the radio nodes are driven by the Arduino processor, so they can be maintained at very lower power, only waking up the Raspberry Pi when required.

The recommended library is the the Radiohead library from Airspayce, as this supports both RFM69 and RFM95 modules. In addition, the radio manager also supports sevaral different types of radio network configuration:

- RHDatagram Addressed, unreliable variable length messages, with optional broadcast facilities.
- RHReliableDatagram Addressed, reliable, retransmitted, acknowledged variable length messages.
- RHRouter Multi-hop delivery from source node to destination node via 0 or more intermediate nodes, with manual routing.
- RHMesh Multi-hop delivery with automatic route discovery and rediscovery.

Great documentation on the library is available [here] (http://www.airspayce.com/mikem/arduino/RadioHead/index.html)

You'll need 2 radios of course, preferably 2 {{<ardhat>}}s :), but you can also use [Jeelink](http://www.digitalsmarties.net/products/jeelink),  [Moteino] (http://lowpowerlab.com/moteino/) or [Teensy] (https://oshpark.com/shared_projects/RIumMBtN) nodes.  Prepare the Ardhat board by attaching the antenna to the board. (The antenna is best left straight but will also work coiled).

Then install the Radiohead [library](https://github.com/Ardhat/Radiohead) into the Arduino library folder, either from the Arduino GUI Library Manager or alternatively from the console using the excellent Platformio code builder, which natively supports both [Radiohead](http://platformio.org/#!/lib/search?query=radiohead) and [{{<ardhat>}}](http://docs.platformio.org/en/latest/platforms/atmelavr.html#boards) .

There are a large number of examples provided with the library, but the RF69_client and RF_69_server are a great starting point.

You'll need to make sure you've set the frequency correctly, in both sketches, depending on the {{<ardhat>}} radio module you have.

Then load up the server Sketch on the 'gateway' {{<ardhat>}}, and the client on the node. On the client, you should get replies to sent message with a RSSI (Received Signal Strength Indication).
