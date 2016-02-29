---
title: Environment Sensor
prev: imu
current: env
next: radio
published: true
---


In addition to the basic functions of Arduino compatibility and power management,  {{<ardhat>}}**-I** has a barometric pressure sensor (or altimeter), which is designed to work in unison with the [IMU](/doc/imu) for motion related applications, such as movement detection and platform stabilization.

The {{<ardhat>}}**-E** includes both pressure and humidity sensing (but without the IMU), for example for use in weather stations.

Both of these functions are performed by Bosch SensorTec integrated environmental sensors, the BMP280 and BME280 respectively, which also include on-board temperature sensors.


From the [Bosch SensorTec website](http://www.bosch-sensortec.com/de/homepage/products_3/environmental_sensors_1/bme280/bme280_1)...

<img align="right" style="width:200px;height:200px; padding-left: 10px; padding-top: 5px" src="/media/BME280.jpg">

> "The humidity sensor features an extremely fast response time which supports performance requirements for emerging applications such as context awareness, and high accuracy over a wide temperature range. The pressure sensor is an absolute barometric pressure sensor with features exceptionally high accuracy and resolution at very low noise. The integrated temperature sensor has been optimized for very low noise and high resolution. It is primarily used for temperature compensation of the pressure and humidity sensors, and can also be used for estimating ambient temperature."

 The BMP280 is largely compatible with the popular [RTIMUlib](https://github.com/Ardhat/RTIMULib-Arduino), but requires some register changes as it was created for the BMP180, the predecessor of the BMP280.


 There's a native BMP280 library written by Kevin Townsend and Limor Fried, of Adafruit fame, on the [Ardhat Github repo](https://github.com/Ardhat/Adafruit_BMP280_Library), and a BME280 version with humidity functions also [available](https://github.com/Ardhat/Adafruit_BME280_Library/blob/master/Adafruit_BME280.cpp).

 The official Bosch driver for BMP280 is on the [Bosch SensorTec Github repo](https://github.com/BoschSensortec/BMP280_driver), as is the  [BME280 driver](https://github.com/BoschSensortec/BME280_driver).

 For more in-depth info on the devices, refer to the [BMP280](https://ae-bst.resource.bosch.com/media/_tech/media/datasheets/BST-BMP280-DS001-12.pdf) and [BME280](https://ae-bst.resource.bosch.com/media/_tech/media/datasheets/BST-BME280_DS001-11.pdf) datasheets.
