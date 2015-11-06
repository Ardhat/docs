---
title: Programming model
prev: installation
current: progmodel
next: upgrading
---

{{<ardhat>}}'s features can be accessed from a compatible host, such as Raspberry Pi, using the [Firmata](https://github.com/firmata/protocol) protocol over serial.

Firmata provides a standardized mechanism to exchange information between a real-time processor such as {{<ardhat>}} and a host, but easily is extended to provide access to the wide range of features available.

As an example, the factory [image](https://github.com/Ardhat/ArdhatFirmata) that ships with {{<ardhat>}} contains a modified version of standard [Arduino Firmata](https://www.arduino.cc/en/Reference/Firmata) that adds several additional features, such as monitoring of the Navigation switch and Status LED control, using the Arduino [SMlib](http://playground.arduino.cc/Code/SMlib). This state machine library provides an extremely lightweight mechanism that allows primitive multitasking.

In principle, an {{<ardhat>}} host application can be written in any language that has a Firmata library, including Processing, Python, C++ and [many more](http://firmata.org/wiki/Download). However, in a Robotics or IoT environment, services are often distributed over a network whose availability cannot be guaranteed. A responsive system cannot  block while  waiting for these services to respond. 

JavaScript’s support of callbacks, and the availability of non-blocking app frameworks such as [node.js](http://nodejs.org/), make it the natural choice for a web enabled system, and it is the main supported framework for local programming of {{<ardhat>}}. Node.js  is built on top of Google’s V8 javascript runtime, and is widely extensible through the use of additional libraries.  The addition of Express and AngularJS allow applications to be exposed over the web if required.

[Johnny-Five](http://johnny-five.io/) is a great node library that sits on top of Firmata but provides some higher level functions to make use with node even easier. For example, {{<ardhat>}} is unit tested using [Mocha](https://mochajs.org/) on Johnny-Five on Firmata. 

Application-specific projects can also be created on top of Node using accessible app generators such as  [Node-Red](http://nodered.org/).

Some of the key libraries are shown below:


**Library** | **Function**
--- | ---
[Johnny-Five](http://johnny-five.io/)| JavaScript Robotics programming framework, by Bocoup
[Mocha](https://mochajs.org/)|is a JavaScript test framework running on Node.js, making asynchronous testing simple and fun.
[Mongodb](http://www.mongodb.org/) | *noSQL database , for example to keep track of authenticated users and nodes* 
[Express](http://expressjs.com/) | *minimal node.js web application framework that provides a robust set of features for web and mobile applications*
[AngularJS](https://angularjs.org/) | *front-end application framework toolset for Single Page Applications*
[Node.js](http://nodejs.org/) | *event-driven, non-blocking back-end javascript environment*
[Firmata](https://github.com/jgautier/firmata) | *node.js library to interact with  local Arduino running the firmata protocol (currently limited to serial port only (use of node-i2c TBD))*
[pi-gpio](https://www.npmjs.com/package/pi-gpio) | *node.js based library to access the GPIO of the Raspberry Pi* 
[socket.io](http://socket.io/) | *real-time bidirectional event-based network communication*
[mqtt](http://mqtt.org/) | *machine-to-machine (M2M)/"Internet of Things" connectivity protocol*
[mosquitto](http://mosquitto.org/) | *message broker for mqtt, supports MQTT,MQTT-SN*
[ponte](https://eclipse.org/ponte/) | *node.js server bridges MQTT, CoAP*
[NeDB](https://github.com/louischatriot/nedb) | *lightweight MongoDB-like noSQL database for node.js*
[freeboard](https://github.com/patchwork-toolkit/patchwork/wiki/Freeboard)  | *local dashboard function*
[Node-Red](http://nodered.org/) | *A visual tool for wiring the Internet of Things*



<div class="note unreleased">
  <h5>IoT System Model </h5>
</div>


The overall system model is as shown below.  

 ![image alt text](/media/IOTmodel.jpg)

The Applications and Services may run on the Pi  (typically written in javascript), or may in part or whole be provided by a cloud service, subscribed to by the Ardhat software, eg [IFTTT](https://ifttt.com/).  Sensor node topology and authentication info is stored in a [NeDB](https://github.com/louischatriot/nedb) a MongoDB-like noSQL database.

The Arduino RealTime code is responsible for monitoring and handling system power, realtime events,  and graceful sleep/shutdown/restart cycles of the Raspberry Pi.  It is also responsible for transmitting application information to the Wireless Sensor Nodes, for example using a simplified MQTT (MQTT-SN) over a link layer protocol such as [TinyHAN](http://www.mike-stirling.com/redmine/projects/tinyhan/) on top of  the relevant PHY (eg RFM96). 
