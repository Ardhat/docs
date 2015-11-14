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

 During normal operation, these devices are typically monitored directly by the Raspberry Pi  but in sleep mode they can be monitored by {{<ardhat>}} and used to wakeup the Raspberry Pi. 

 For **much** more information on programming see [this Article](https://github.com/Ardhat/MPU-9250) from Kris Winer, with an accompanying sketch [here](https://github.com/Ardhat/MPU-9250) that you can use if you want to drive the IMU directly from {{<ardhat>}}.

 The MPU9250 is also compatible with the popular [RTIMUlib](https://github.com/richards-tech/RTIMULib-Arduino).
 
 {{<ardhat>}}'s  high performance IMU, together with Real-Time processing, PWM and analogue sensing , are essential requirements for the core of any robotics system. For those who like a challenge, one of the most interesting robot variants is the the 3D Balance Bot, more commonly called a [BallBot](https://en.wikipedia.org/wiki/Ballbot).  This concept was originally rendered in Mindstorms by  [Takashi Chikamasa](http://lejos-osek.sourceforge.net/),  using a Lejos, a custom Real-Time kernel for Mindstorms.

 <div class=video-container>
<iframe src="https://www.youtube.com/embed/f8jxGsg3p0Y" frameborder="0" allowfullscreen></iframe>
</div>

 We've updated the concept to Mindstorms EV3 using {{<ardhat>}}, a motor shield and a 3-cell LiPo,

 ![image alt text](/media/balbot.jpg)

 More details, including Lego Digital designer build instructions and code are in the {{<ardhat>}} Github repository.

![image alt text](/media/balbot.jpg)




