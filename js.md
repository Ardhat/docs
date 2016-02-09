---
title: Javascript & Node.js®
prev: python
current: js
next: upgrading
published: true
---

{{<ardhat>}}'s features can be accessed from a compatible host, such as Raspberry Pi, using the [Firmata](https://github.com/firmata/protocol) protocol over serial (for more information see [Programming Model](/doc/progmodel/)).

Firmata provides a standardized mechanism to exchange information between a real-time processor such as {{<ardhat>}} and a host, useable by many programming languages.

Javascript is an interpreted language like Python, and therefore relies on an interpreter to be running to execute its functions. The most common javascript interpreter is the web browser, and one of the fastest is the one built into Google's Chrome browser.

Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine, and uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. The Node.js 200,000+ package ecosystem, npm, is the [largest ecosystem](http://www.modulecounts.com/) of open source libraries in the world.

<a href="http://johnny-five.io/"><img align="right" style="height:200px; padding-left: 10px; padding-top: 5px" src="/media/johnnyfive.png" alt="Johnny Five" title="Johnny Five"></a> One of those many libraries includes [node firmata](https://github.com/jgautier/firmata), which means that once node.js is installed, we can use the wide range of node packages directly with {{<ardhat>}}'s hardware, allowing the rapid creation of web-based sensor systems.

In this example we are going to use
[Johnny-Five](http://johnny-five.io/), which uses node firmata, and is an excellent programming framework which abstracts the hardware and makes cloud connected device programming much easier.  

&nbsp;


### Using Node Firmata with Ardhat

Raspian Jessie comes with a version of Node.js installed; unfortunately it is an older version (0.10.29 at the time of writing) that does not play well with many newer libraries, so we need to remove it and reinstall a newer version of Node.js such as v0.12.x or v4.2.x together with npm.

To do this we must uninstall the built-in version and re-install using the instructions below.  

<div class="note info">
  <p>To enter these commands more easily, connect to the Pi using `ssh`, so that you can copy and paste them into the terminal.</p>
</div>


First we remove all the built in packages (but leave your current workspace if any, which by default is at ~/.node-red) .

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Uninstall legacy node</p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo apt-get remove nodered</span>
        </p>        
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo apt-get remove nodejs nodejs-legacy</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo apt-get remove npm  </span>
        </p>
        <p class="line">
          <span class="output"> # if you installed npm</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>



Now we can proceed to re-install Node.js following the instructions below depending on your processor type. (As the Pi 2 uses a different processor (Arm v7) compared with the original Pi (Arm v6) the method of installing node.js is slightly different).

&nbsp;

**Raspberry Pi 2**
<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title"> Install Node.js on Raspberry Pi 2 - and other Arm7 processor based boards</p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">curl -sL https://deb.nodesource.com/setup_4.x | sudo bash -</span>
        </p>        
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo apt-get install -y build-essential python-dev python-rpi.gpio nodejs</span>
        </p>
        <p class="line">
          <span class="output">This also installs some additional dependencies.</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>

&nbsp;

**Pi (version 1), Pi Zero, Pi A+/B+**

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Install Node.js on Pi (version 1), Pi Zero, Pi A+/B+</p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">wget http://node-arm.herokuapp.com/node_archive_armhf.deb</span>
        </p>        
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo npm cache clean</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo dpkg -i node_archive_armhf.deb</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo apt-get install build-essential python-dev python-rpi.gpio</span>
        </p>
        <p class="line">
          <span class="output">This also installs some additional dependencies.</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title"> Install the latest stable version of Node-RED and Johnny-Five</p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo npm install -g --unsafe-perm  node-red </span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">npm install johnny-five </span>
        </p>       
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>

Now we are ready to run our javascript program on node.js driving Ardhat.


Create a file with the following contents:

~~~c
var five = require("johnny-five"),
    board = new five.Board({ port: "/dev/ttyS0" });

board.on("ready", function() {
  // Create an Led on pin 9
  var led = new five.Led(9);

  // Strobe the pin on/off, defaults to 100ms phases
  led.strobe();
});

~~~


Save it as test.js, and run it with


<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title"> Run the test Javascript program</p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">node test.js</span>
        </p>   
        <p class="line">
          <span class="output">1455005904950 Connected /dev/ttyS0</span>
        </p>
        <p class="line">
          <span class="output">1455005910077 Repl Initialized </span>
        </p>
        <p class="line">
          <span class="output">>></span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>



Ardhat's activity LED will blink quickly.

"Repl Initialized" means that the Johnny-Five "Read Evaluate Print Loop" is running, which means that you have a node prompt at which you can enter [node commands](http://johnny-five.io/examples/repl/).

For a more in-depth example, see this [article](https://www.smashingmagazine.com/2016/02/hardware-hacking-with-javascript-internet-of-things/) which shows how to build a simple [home-monitoring system](https://www.smashingmagazine.com/2016/02/hardware-hacking-with-javascript-internet-of-things/#home-monitoring), similar to commercial products like Nest and Hive.

<a href="https://www.smashingmagazine.com/2016/02/hardware-hacking-with-javascript-internet-of-things/#home-monitoring"><img  style="height:200px" src="/media/diynest.jpg" alt="DIYnest" title="DIYnest"></a>



&nbsp;

<a href="http://nodered.org/"><img align="right" style="height:200px; padding-left: 10px; padding-top: 5px" src="/media/node-red-screenshot-sm.png" alt="NodeRED" title="NodeRED"></a>
An alternative to programming in javascript directly is to use the visual programming approach offered by Node-RED.

Node-RED provides a browser-based flow editor that makes it easy to wire together flows using the wide of range nodes in a 'palette' of node modules. Flows can then be deployed in a single-click. For more info see the [Node-Red website](http://nodered.org/) .
