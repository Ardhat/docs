---
title: I/O usage
prev: leds
current: io
next: battery
published: true
---



{{<ardhat>}} has full Arduino Shield compatibility, as well as being Raspberry Pi HAT compliant. Some of the pins have a special usage in the {{<ardhat>}} environment as detailed below:  

 **Raspberry Pi GPIO** | Usage
--- | ---
**GPIO 2** | I2C-SDA –  I2C bus for communication with RTC, IMU, ENV and Arduino
**GPIO 3** | I2C-SCL –  I2C bus for communication with RTC, IMU, ENV and Arduino
**GPIO 14** | Serial RXD – used for programming the Arduino with GPIO 22
**GPIO 15** | Serial TXD – used for programming the Arduino with GPIO 22
**GPIO 18** | PiPWM – connected to a 3V-5V level shifter to drive e.g. WS2811 LED strips (see **SPARE** below)
**GPIO 22** | Arduino ‘Reset’ line – used for programming with serial port
**ID_SC** | HAT EEPROM Clock – used for read-writing the ArdHAT EEPROM
**ID_SD** | HAT EEPROM Data – used for read-writing the ArdHAT EEPROM
**5V** | Connected to Ardhat 5V through a MOSFET switch controlled by Ardhat A3 (see below) NB even when the switch is off current can flow from the Raspberry Pi to Ardhat  

<br>
The table below shows the shield I/O usage by {{<ardhat>}}. Unlike a standard Arduino, the processor used has 2 extra analog I/O , A6 and A7, which are used for battery and supply monitoring, and which are connected to the pins normally used by A4 and A5, in case you want to access these signals in your applications.
The standard A4 and A5 pins are brought out, as in Arduino Uno, to the shield SDA and SCL pins as they are permanently assigned to I2C.
<br><br>

**Arduino Shield I/O** | Usage
--- | ---
**D0** | serial data from Raspberry Pi
**D1** | serial data to Raspberry Pi
**D3** | Radio and peripheral Interrupt
**D10*** | Radio node SPI SS
**D11*** | Radio node SPI MOSI
**D12*** | Radio node SPI MISO
**D13*** | Radio node SPI SCK
**A3** | PowerOn/Off  to Raspberry Pi
**A4** | Connected to A6, External supply voltage monitor
**A5** | Connected to A7, Power/Nav Switch and LiPo  voltage  monitor
**Vin** | Connected to the 2.1mm DC Jack through polarity protection
**5V** | Supplied either from the Ext-> 5V Buck converter, or the LiPo->5V Boost converter or the Raspberry Pi MicroUSB 5V supply
**3.3V** | Supplied through a 300mA linear regulator on Ardhat (NB if fitted, the radio module may consume 150mA peak during transmission bursts)
**SPARE** | The unused shield pin next to IOREF is the 5V level shifted O/P from GPIO18 (PiPWM) (see above)
**AREF** | AVR analog reference voltage
**SCL** | I2C SDA to Raspberry Pi and Peripherals (A4 on standard Arduino)
**SDA** | I2C SCL to Raspberry Pi and Peripherals (A5 on standard Arduino)

<div class="note info">
  <p>The pins above marked * are available for use if the radio module is not fitted.</p>
</div>


**Additional** | Usage
--- | ---
**ICSP Header** | Standard Arduino programming header can be used e.g. for burning new bootloader
**Solar** | 0.1" header next to ICSP can be connected to a 6V solar panel to charge the LiPo cell while Raspberry Pi is turned off and Ardhat is on sleep mode
**RTC Clock Out** | PCF8653 RTC can be programmed to generate a Clock O/P on the test point next to Pi GPIO26
