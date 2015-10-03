---
title: Expansion
---

### Arduino Compatibility

Ardhat contains a complete Arduino Uno R3 compatible subsystem clocked at 16MHz.  Most newer technologies, including the Raspberry Pi itself,  operate at 3.3V. This can be a problem when connecting to common real world systems like servos and Smart LEDs that operate at 5V.  Ardhat has the necessary interface circuitry to act as a bridge between the 5V and 3V worlds, allowing the Raspberry Pi to connect with either system type. The Ardhat board may also be operated independently of a Raspberry Pi by powering it from either an external supply or the built in LiPo.

### Arduino Shield Support

Ardhat supports all Uno compatible shields. AVR SPI is available on the ICSP header which is used by the majority of shields that require SPI.  The latest R3 features such as IOREF are included.

### Raspberry Pi <> Arduino communication

The Raspberry Pi and Arduino can communicate over both Serial and I2C. Serial is used for the main inter-processor communication, and the Arduino can be programmed using the Arduino IDE through the Raspberry Pi serial port. DTR emulation is provided using Raspberry Pi GPIO 13.

When the Raspberry Pi is active, it is the master on the  I2C bus, and is responsible for setup of the Ardhat  I2C peripherals (IMU, Altimeter, RTC).  When the Raspberry Pi is inactive, the Arduino can master the bus and interrogate the peripherals.  For example by watching the RTC, the Raspberry Pi can be started when the next crontab entry is about to come due.