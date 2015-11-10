---
title: IMU
prev: rtc
current: imu
next: env
published: true
---


### (Inertial Measurement Unit)  

![image alt text](/media/mpu9250.jpg)

The IMU is connected to the I2C bus. It is mounted at {{<ardhat>}}'s  geographic center to avoid offset errors. It consists of an Invensense MPU9250, which provides

* 3-axis accelerometer
* 3-axis gyroscope
* 3-axis magnetometer (compass) 

 During normal operation, these devices are monitored directly by the Raspberry Pi  but in sleep mode they can be monitored by {{<ardhat>}} and used to wakeup the Raspberry Pi. 

 For **much** more information on programming see [this Article](https://github.com/Ardhat/MPU-9250) from Kriswiner, with an accompanying sketch [here](https://github.com/Ardhat/MPU-9250) that you can use if you want to drive the IMU directly from {{<Ardhat>}}.

 The MPU9250 is also compatible with the popular [RTIMUlib](https://github.com/richards-tech/RTIMULib-Arduino).
 
With a simple motor shield in place this makes possible 3D balancing bots, more commonly called Ballbots, using Lego Mindstorms

 ![image alt text](/media/balbot.jpg)