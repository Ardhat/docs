---
title: Interprocessor Comms
published: true
---

## Raspberry Pi <> Arduino communication

The Raspberry Pi and Arduino can communicate over both Serial and I2C. Serial is used for the main inter-processor communication, and the Arduino can be programmed using the Arduino IDE through the Raspberry Pi serial port. DTR emulation is provided using Raspberry Pi GPIO 13.

When the Raspberry Pi is active, it is the master on the  I2C bus, and is responsible for setup of the Ardhat  I2C peripherals (IMU, Altimeter, RTC).  When the Raspberry Pi is inactive, the Arduino can master the bus and interrogate the peripherals.  For example by watching the RTC, the Raspberry Pi can be started when the next crontab entry is about to come due.

Layered on top of the physical layer is Firmata, which is the Data Link layer in [OSI parlance](https://en.wikipedia.org/wiki/OSI_model).

Applications on the Pi can thus communicate with the {{<ardhat>}} provided they have a Firmata language binding.

Although javascript is the recommended language,(using the node.js Firmata library) other languages such as Python can easily be used.

## Python Firmata with Ardhat

Ardhat ships from the factory with Firmata already installed, but follow the instructions in [_Installation_](/docs/installation) to make sure you have turned off kernel serial port use first.

To install Firmata on the host connect to the Pi using ssh, so that you can copy and paste the following into the terminal:

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Python Firmata</p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo apt-get install python-pip python-serial</span>
        </p>        
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo pip install pyfirmata</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">python</span>
        </p>
        <p class="line">
          <span class="output"># => You should now have a python prompt >>></span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>

At the Python prompt we can then instantiate a board, and set and get values on {{<ardhat>}}.

To read the value on an analog pin, you have to first turn on the analog value reporting for that pin. 

Note that 
- Analogue reads and PWM writes are normalized to a 0 .. 1 range, and not the standard Arduino 0 .. 255 and 0 .. 1023.
- You really need to start a separate iterator thread to stop old readings overflowing the serial buffer

These commands will get you up and running reading Analog port 0.

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Python Firmata</p>
      <div class="shell">
        <p class="line">
          <span class="prompt">>>></span>
          <span class="command">from pyfirmata import Arduino, util</span>
        </p>        
        <p class="line">
          <span class="prompt">>>></span>
          <span class="command">board = Arduino('/dev/ttyS0')</span>
        </p>
        <p class="line">
          <span class="prompt">>>></span>
          <span class="command">it = util.Iterator(board)</span>
        </p>
        <p class="line">
          <p class="line">
          <span class="prompt">>>></span>
          <span class="command">it.start</span>
        </p>
          <p class="line">
          <span class="prompt">>>></span>
          <span class="command">board.analog[0].read()</span>
        </p>
        <p class="line">
        <p class="line">
          <span class="output"># => You can repeat the above command to show the current output of Analog Port 0</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>



