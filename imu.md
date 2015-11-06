---
title: IMU
prev: rtc
current: imu
next: env
---

### (Inertial Measurement Unit)  

![image alt text](/media/mpu9250.jpg)

The IMU is connected to the I2C bus. It is mounted at {{<ardhat>}}'s  geographic center to avoid offset errors. It consists of an Invensense MPU9250, which provides

* 3-axis accelerometer
* 3-axis gyroscope
* 3-axis magnetometer (compass) 


 ![image alt text](/media/balbot.jpg)

 During normal operation, these devices are monitored directly by the Raspberry Pi  but in sleep mode they can be monitored by {{<ardhat>}} and used to wakeup the Raspberry Pi. 

 The MPU9250 is compatible with the popular [RTIMUlib](https://github.com/richards-tech/RTIMULib-Arduino)