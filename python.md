---
title: Python
prev: progmodel
current: python
next: js
published: true
---



{{<ardhat>}}'s features can be accessed from a compatible host, such as Raspberry Pi, using the [Firmata](https://github.com/firmata/protocol) protocol over serial (for more information see [Programming Model](/doc/progmodel/)).

Firmata provides a standardized mechanism to exchange information between a real-time processor such as {{<ardhat>}} and a host, useable by many programming languages.


### Using Python Firmata with Ardhat

{{<ardhat>}} ships from the factory with Firmata already installed (but follow the instructions in [_Installation_](/doc/installation) to make sure you have turned off kernel serial port use before proceeding). We need to install a couple of extra packages to allow the host to communicate over Firmata using Python.

<div class="note info">
  <p>To enter these commands more easily, connect to the Pi using `ssh`, so that you can copy and paste them into the terminal.</p>
</div>



<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Setting up Python Firmata</p>
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

- You should start a separate iterator thread to stop unread value reports clogging up the Firmata channel


As an example, the following Python commands let you perform a simple test of port D2.

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">At the Python Prompt... </p>
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
          <span class="command">board.digital[2].write(1)</span>
        </p>
        <p class="line">
          <p class="line">
          <span class="prompt">>>></span>
          <span class="command">board.digital[2].read()</span>
        </p>
        <p class="line">
          <span class="command">1</span>
        </p>
        <p class="line">
        <p class="line">
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>



... or use this example for reading Analog port 0.

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">At the Python Prompt... </p>
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
          <span class="command"> board.analog[0].enable_reporting()</span>
        </p>
        <p class="line">
          <span class="prompt">>>></span>
          <span class="command">board.analog[0].read()</span>
        </p>
        <p class="line">
          <span class="command">0.2727</span>
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




More info on using Python Firmata can be found [here](https://github.com/tino/pyFirmata).
