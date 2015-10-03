---
title: Navigation Switch
---

The navigation switch is connected to the AVR analog port A7. This port is not present on a standard Arduino, so does not affect normal sketch operation.

When operated, the switch forms a potential divider from the output of the LiPo charger, as shown in the following table:

 **Navigation Switch** | 
--- | ---
**Open** | 5V (= 1024) or LiPo voltage when running on battery
**Left** | 2/3 open circuit voltage
**Right** | 1/3 open circuit voltage
**Pressed** | 0V
