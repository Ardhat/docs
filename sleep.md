---
title: Sleep Management
prev: upgrading
current: sleep
next: github
---

## Power/Sleep Management

{{<ardhat>}} performs a handshake with the Raspberry Pi to perform a graceful shutdown. This can be triggered by external events, such as operation of the power/sleep switch, or internal events such as crontab entries.

When a shutdown is required, an exchange takes place between the Power Monitor daemon on the Raspberry Pi, and the {{<ardhat>}} Realtime, using the Firmata communication channel (this can be over serial or  I2C, see below). The Raspberry Pi can schedule wakeup requests by adding entries in the crontab; during this exchange the next entry in the crontab before shutdown is transferred to the Arduino for wakeup calls.

The Raspberry Pi RUN status is monitored by {{<ardhat>}}. Once {{<ardhat>}} has detected that the OS is no longer running it can physically cut the power from the Raspberry Pi and enter low power mode. In this mode the current consumption of the system is less than 100µA. This provides over a year of standby operation using the standard 2200mAh LiPo cell.

The power is cut to the Raspberry Pi by setting {{<ardhat>}} port A3 high.


<div class="note">
  <p>Note that the Raspberry Pi will not turn off if it is connected to USB power on its micro-USB connector.
Also note that power from the Raspberry Pi will always be supplied to {{<ardhat>}} even if this switch is off.</p>
</div>


The IMU and RTC can both be setup to generate interrupts to wakeup the system, see below.
