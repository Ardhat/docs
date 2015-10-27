---
title: I/O usage
prev: leds
current: io
next: battery
published: true
---



 **Raspberry Pi GPIO** | 
--- | ---
**GPIO 2** | I2C-SDA –  I2C bus for communication with RTC, IMU and Arduino
**GPIO 3** | I2C-SCL –  I2C bus for communication with RTC, IMU and Arduino
**GPIO 14** | Serial RXD – used for programming the Arduino with GPIO 13
**GPIO 15** | Serial TXD – used for programming the Arduino with GPIO 13
**GPIO 22** | Arduino ‘Reset’ line – used for programming with serial port




**Arduino I/O** | 
--- | ---
**D0** | serial data from Raspberry Pi
**D1** | serial data to Raspberry Pi
**D3*** | Radio and peripheral Interrupt
**D10*** | Radio node SPI SS
**D11*** | Radio node SPI MOSI
**D12*** | Radio node SPI MISO
**D13*** | Radio node SPI SCK
**A3** | PowerOn/Off  to Raspberry Pi
**A4** | I2C SDA to Raspberry Pi
**A5** | I2C SCL to Raspberry Pi
**A6** | External supply voltage monitor
**A7** | Power/Nav Switch and LiPo  voltage  monitor
