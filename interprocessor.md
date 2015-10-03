---
title: Interprocessor Comms

---
## Raspberry Pi <> Arduino communication

The Raspberry Pi and Arduino can communicate over both Serial and I2C. Serial is used for the main inter-processor communication, and the Arduino can be programmed using the Arduino IDE through the Raspberry Pi serial port. DTR emulation is provided using Raspberry Pi GPIO 13.

When the Raspberry Pi is active, it is the master on the  I2C bus, and is responsible for setup of the Ardhat  I2C peripherals (IMU, Altimeter, RTC).  When the Raspberry Pi is inactive, the Arduino can master the bus and interrogate the peripherals.  For example by watching the RTC, the Raspberry Pi can be started when the next crontab entry is about to come due.