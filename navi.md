---
title: Navigation Switch
prev: github
current: navi
next: rtc
---

The navigation switch is connected to the AVR analog port A7. This port is not present on a standard Arduino, so does not affect normal sketch operation.

When operated, the switch forms a potential divider from the output of the LiPo charger, as shown in the following table:

 **Navigation Switch** | **Ardhat Port A7**
--- | ---
**Open** | 5V (= 1024) or LiPo voltage when running on battery
**Left** | 2/3 open circuit voltage
**Right** | 1/3 open circuit voltage
**Pressed** | 0V

<br>

As an example, the default factory firmware uses the Nav switch to toggle power to the host, eg Raspberry Pi. You can this use as a starting point for your own applications using the source code on the [Ardhat Github repo](https://github.com/Ardhat/ArdhatFirmata).

<div class="note info">
  <p>The factory firmware image can easily be expanded to include additional functions, for example sending message to the Pi over the Firmata interface. </p>
</div>
