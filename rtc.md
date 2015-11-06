---
title: Real Time Clock
prev: navi
current: rtc
next: imu
---
The realtime clock is provided by an NXP PCF8563, which is supported directly by the Raspberry Pi Linux distribution for use as a hardware clock. This is battery backed by the on board LiPo cell. The RTC time can be set manually or automatically updated  from an NTP server  when this is available. When the Raspberry Pi is halted, {{<ardhat>}} can access the RTC to in order to wake up the Raspberry Pi at a predetermined time. 

The PCF8563 features, taken from the [product datasheet](http://www.nxp.com/documents/data_sheet/PCF8563.pdf), are:

- Provides year, month, day, weekday, hours, minutes, and seconds based on a 32.768kHz quartz crystal
- Century flag
- Clock operating voltage: 1.0V to 5.5V at room temperature
- Low backup current; typical 0.25uA at VDD = 3.0V and Tamb = 25°C
- 400kHz two-wire I2C-bus interface (at VDD = 1.8V to 5.5V)
- Programmable clock output for peripheral devices (32.768kHz, 1.024kHz, 32Hz, and 1Hz)
- Alarm and timer functions


In order to use the PCF8563 as a hardware system clock for Raspberry Pi we need to make sure the kernel modules are loaded at boot time...

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Edit /etc/modules to include pcf8563 </p>
      <div class="shell">
         <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo nano /etc/modules</span>
        </p>
                 <p class="line">
 <br># /etc/modules: kernel modules to load at boot time.<br>
 #<br>
 # This file contains the names of kernel modules that should be loaded<br>
 # at boot time, one per line. Lines beginning with "#" are ignored.<br>
 # Parameters can be specified after the module name.<br>
<br>
snd-bcm2835<br>
i2c-bcm2708<br>
i2c-dev<br>
rtc-pcf8563<br>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>

...and that the hwclock is loaded at startup

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Edit /etc/rc.local to end as shown...</p>
      <div class="shell">
         <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo nano /etc/rc.local</span>
        </p>
                 <p class="line">
<br>                 
modprobe i2c-bcm2708<br>
echo pcf8563 0x51 > /sys/class/i2c-adapter/i2c-1/new_device<br>
modprobe rtc-pcf8563<br>
hwclock -s<br>
<br>
exit 0<br>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>

Save, then reboot with `sudo reboot`


Now you can check the results, first with `i2detect -y 1`, which shows that the i2c driver loaded (and that in this case we have 3 i2c devices present)

<img align="center" src="/media/i2cdetect.png">

Then with `sudo hwclock --rtc /dev/rtc0 -r --debug`

<img align="center" src="/media/rtc-check.png">









