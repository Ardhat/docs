---
title: I/O usage
prev: leds
current: io
next: battery
published: true
---



 **Raspberry Pi GPIO** | Usage
--- | ---
**GPIO 2** | I2C-SDA –  I2C bus for communication with RTC, IMU and Arduino
**GPIO 3** | I2C-SCL –  I2C bus for communication with RTC, IMU and Arduino
**GPIO 14** | Serial RXD – used for programming the Arduino with GPIO 13
**GPIO 15** | Serial TXD – used for programming the Arduino with GPIO 13
**GPIO 18** | PiPWM – connected to a 3V-5V level shifter to drive e.g. WS2811 LED strips (see **SPARE** below)
**GPIO 22** | Arduino ‘Reset’ line – used for programming with serial port
**ID_SC** | HAT EEPROM Clock – used for read-writing the ArdHAT EEPROM
**ID_SD** | HAT EEPROM Data – used for read-writing the ArdHAT EEPROM
**5V** | Connected to Ardhat 5V through a MOSFET switch controlled by Ardhat A3 (see below) NB even when the switch is off current can flow from the Raspberry Pi to Ardhat  

<br />

**Arduino I/O** | Usage
--- | ---
**D0** | serial data from Raspberry Pi
**D1** | serial data to Raspberry Pi
**D3** | Radio and peripheral Interrupt
**D10*** | Radio node SPI SS
**D11*** | Radio node SPI MOSI
**D12*** | Radio node SPI MISO
**D13*** | Radio node SPI SCK
**A3** | PowerOn/Off  to Raspberry Pi
**A4** | I2C SDA to Raspberry Pi
**A5** | I2C SCL to Raspberry Pi
**A6** | External supply voltage monitor
**A7** | Power/Nav Switch and LiPo  voltage  monitor
**Vin** | Connected to the 2.1mm DC Jack through polarity protection
**5V** | Supplied either from the DC buck converter, or the LiPo->5V Boost converter or the Raspberry Pi Micros USB 5V
**3.3V** | Supplied through a 300mA linear regulator on Ardhat (NB if fitted, the radio module may consume 150mA peak during transmission bursts)
**SPARE** | The unused shield pin next to IOREF is the 5V level shifted O/P from the GPIO18 (PiPWM) (see above)


*These pins are available for use if the radio module is not fitted.