---
title: Programming model
prev: installation
current: progmodel
next: upgrading
---

Ardhat employs a future-proof programming environment ready for large distributed node networks.

In principle, an application can be written in any language that can access the Raspberry Pi hardware (e.g. GPIOs, I2C, network etc). However, in an IoT environment, services are often distributed over a network whose availability cannot be guaranteed. A responsive system cannot  block while  waiting for these services to respond. 

JavaScript’s support of callbacks, and the availability of non-blocking app frameworks such as [node.js](http://nodejs.org/), make it the natural choice for a web enabled system such as Ardhat.  

The Ardhat programming framework uses javascript in a [MEAN](http://mean.io/#!/) (MongoDB, Express, Angular, Node) environment, which is a set of technologies that work well together to allow the creation of distributed web-enabled applications. 

The main supported framework for local programming of Ardhat is [Node.js](http://nodejs.org/), which is built on top of Google’s V8 javascript runtime, and is widely extensible through the use of additional libraries.  The addition of Express and AngularJs allow applications to be exposed over the web if required. Some of the key libraries are shown below:


**Library** | **Function**
--- | ---
[Mongodb](http://www.mongodb.org/) | *noSQL database , for example to keep track of authenticated users and nodes* 
[Express](http://expressjs.com/) | *minimal node.js web application framework that provides a robust set of features for web and mobile applications*
[AngularJS](https://angularjs.org/) | *front-end application framework toolset for Single Page Applications*
[Node.js](http://nodejs.org/) | *event-driven, non-blocking back-end javascript environment*
[firmata](https://github.com/jgautier/firmata) | *node.js library to interact with  local Arduino running the firmata protocol (currently limited to serial port only (use of node-i2c TBD))*
[pi-gpio](https://www.npmjs.com/package/pi-gpio) | *node.js based library to access the GPIO of the Raspberry Pi* 
[socket.io](http://socket.io/) | *real-time bidirectional event-based network communication*
[mqtt](http://mqtt.org/) | *machine-to-machine (M2M)/"Internet of Things" connectivity protocol*
[mosquitto](http://mosquitto.org/) | *message broker for mqtt, supports MQTT,MQTT-SN*
[ponte](https://eclipse.org/ponte/) | *node.js server bridges MQTT, CoAP*
[NeDB](https://github.com/louischatriot/nedb) | *lightweight MongoDB-like noSQL database for node.js*
[freeboard](https://github.com/patchwork-toolkit/patchwork/wiki/Freeboard)  | *local dashboard function*



Application-specific user flows  can be written on top of this framework using accessible app generators such as  [Node-Red](http://nodered.org/) or [Emoncms](http://emoncms.org/).

<div class="note unreleased">
  <h5>IoT System Model </h5>
</div>


The overall system model is as shown below.  

 ![image alt text](/media/IOTmodel.jpg)

The Applications and Services may run on the Pi  (typically written in javascript), or may in part or whole be provided by a cloud service, subscribed to by the Ardhat software, eg [IFTTT](https://ifttt.com/).  Sensor node topology and authentication info is stored in a [NeDB](https://github.com/louischatriot/nedb) a MongoDB-like noSQL database.

The Arduino RealTime code is responsible for monitoring and handling system power, realtime events,  and graceful sleep/shutdown/restart cycles of the Raspberry Pi.  It is also responsible for transmitting application information to the Wireless Sensor Nodes, for example using a simplified MQTT (MQTT-SN) over a link layer protocol such as [TinyHAN](http://www.mike-stirling.com/redmine/projects/tinyhan/) on top of  the relevant PHY (eg RFM96). 
