---
title: Real Time Clock
permalink: /docs/sites/
---
The realtime clock is provided by an NXP PCF8563, which is supported directly by the Raspberry Pi Linux distribution for use as a hardware clock. This is battery backed by the on board LiPo cell. The RTC time can be set manually or automatically updated  from an NTP server  when this is available. When the Raspberry Pi is halted, the Arduino can access the RTC to in order to wake up the Raspberry Pi at a predetermined time. 