---
category: Getting Started
title: Overview
weight: 30
toc: true
prev: quickstart
current: overview
next: configuration
---

 ![image alt text](/media/ardhat_bottom.jpg)

On a single Raspberry Pi standard [HAT](https://github.com/raspberrypi/hats),  {{<ardhat>}} integrates not only an [Arduino Uno ](http://arduino.cc/en/Main/arduinoBoardUno)compatible real-time hardware subsystem,  but also a complete power management solution, a full suite of environmental sensors, and an optional long-range wireless mesh network node.


Ardhat supports an open,  state-of-the-art software framework that securely and flexibly allows Sensors and Actuators to communicate both amongst themselves, and with other  Sensor Network devices and products, on or off the Internet.

Compatible with all current Raspberry Pi models, Ardhat adds the environmental  protection and awareness, real-time performance, and  low-power operation that a real world system needs.

### {{<ardhat>}} -Features

* * *



**Features** | **Benefits**
--- | ---
Full LiPo charge control system  | *High-current safe charging and operation from 3.7V LiPo cell*
8-28V input voltage range power converter with battery reversal protection | *Wide voltage range allows Raspberry Pi use in automotive applications. Standard DC Power Jack*
High Power 5V output | *3A 5V output available for driving peripherals, eg ESC*
Power/Sleep/Navigation Switch | *3-position nav switch for power/sleep//UI applications use*
10-DOF IMU Sensor Fusion devices | *Accelerometer, Magnetometer, Gyroscope, Barometer, Thermometer give Raspberry Pi situational awareness*
Battery backed Real time Clock | *Raspberry Pi keeps correct time/date when off-net; Ardhat can wake Raspberry Pi at timed intervals or set time*
Long-Range Wireless Mesh Node | *Up to 10km range  ISM band radio ( 433, 868, or 915MHz for worldwide use - optional)*
Complete Raspberry Pi  Power  Management | *Timer/IMU/LoRa Radio event driven startup e.g. for time-lapse photography*
Arduino Uno compatible Shield pinout | *Use wide variety of Arduino ecosystem hardware with RAspberry Pi. Accepts all 5V shields.  Can run standalone.* 
12-channel PWM | *Raspberry Pi can use Ardhat 5V PWM over I2C*
6 channel analogue in | *Raspberry Pi can use Ardhat Analogue Inputs over I2C*
Smart LED (e.g. NeoPixel) Output | *Provides 5V GPIO from RPi for ‘ZeroCPU’ addressable LEDs*
‘BatteryOnTop’ design | *Flat upper surface for compact, secure battery storage*
Comprehensive Charge Monitoring | *As well as visual feedback, RPi can read both external and battery  voltages over I2C*
Programmable Wake-up and Watchdog power management | *Raspberry Pi can be woken at predetermined times; watchdog function increases system robustness*
Inter-processor communication over Hi-Speed 400kHz I2C bus | *Rapid and efficient communication between Raspberry Pi and Ardhat* 
On board peripherals are accessible by both Arduino and Raspberry Pi | *When Raspberry Pi is in halt mode, Ardhat can check peripherals and wake up Raspberry Pi  e.g. RTC, IMU*
Raspberry Pi Hat standard compliant design | *Fully compliant, with  ID EEPROM ,40 pin header compatible with Raspberry Pi model A+ , B+ and B V2*

<br/>

Note: Ardhat does not include peripherals that are available off-the-shelf, such as WiFi,  Bluetooth, GPS, storage, camera etc. as these are cheaper and easier to install using the Raspberry Pi USB port(s).  
