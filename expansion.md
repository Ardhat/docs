---
title: Expansion
prev: battery
current: expansion
next: installation
---

### Arduino Compatibility

{{<ardhat>}} contains a complete Arduino Uno R3 compatible subsystem clocked at 16MHz.  Most newer technologies, including the Raspberry Pi itself,  operate at 3.3V. This can be a problem when connecting to common real world systems like servos and Smart LEDs that operate at 5V.  {{<ardhat>}} has the necessary interface circuitry to act as a bridge between the 5V and 3V worlds, allowing the Raspberry Pi to connect with either system type. {{<ardhat>}} may also be operated independently of a Raspberry Pi by powering it from either an external supply or the built in LiPo.

### Arduino Shield Support

{{<ardhat>}} supports all Uno compatible shields. AVR SPI is available on the ICSP header which is used by the majority of shields that require SPI.  The latest R3 features such as IOREF are included. For more information see the [IO usage page] (/doc/io/)

### Raspberry Pi <> {{<ardhat>}} communication

The Raspberry Pi and Arduino can communicate over both Serial and I2C. Serial is used for the main inter-processor communication, and {{<ardhat>}} can be programmed using the Arduino IDE through the Raspberry Pi serial port. DTR emulation is provided using Raspberry Pi GPIO 22.

When the Raspberry Pi is active, it is the master on the  I2C bus, and is responsible for setup of the {{<ardhat>}}  I2C peripherals (e.g.IMU, Altimeter, RTC etc.).  When the Raspberry Pi is inactive, {{<ardhat>}} can master the bus and interrogate the peripherals.  For example by watching the RTC, the Raspberry Pi can be started when the next crontab entry is about to come due.