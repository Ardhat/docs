---
title: Installation
weight: 30
toc: true
prev: expansion
current: installation
next: progmodel
---


Getting Ardhat installed and ready-to-go should only take a few minutes.

The Optiboot bootloader is already installed on {{<ardhat>}}'s processor, but we need to make sure the Raspberry Pi is setup correctly, and has the necessary software in place.

By default, Raspberry Pi connects it's console ouput to the serial port. As we use this channel to communicate we need to disable it. This is most easily doen with the in-built utility raspi-config.


<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Setup Pi Hardware</p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo raspi-config</span>
        </p>        
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>

From the menu, select _Advanced Options_

![image alt text](/media/raspi-config.png)


Then select serial

![image alt text](/media/raspi-config-serial.png)

and disable shell and kernel messages on serial

![image alt text](/media/raspi-config-serial-no.png)

Back at the Advanced Option menu you'll also want to enable I2C, so that you can access the Ardhat peripeherals directly if required

![image alt text](/media/raspi-config-I2C.png)


Now we need to load a few software pre-requisites, which are best installed from the command line, and the best way to do that is to ssh into the Raspberry Pi Linux instance, so that you can copy and paste the commands below into your terminal

First make sure you have up-to-date packages installed

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Update Packages</p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo apt-get update</span>
        </p>        
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo apt-get upgrade</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>

Then install some essential packages, including a modified version of avrdude.

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Install a few essentials </p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo aptitude install git arduino</span>
        </p>        
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">git clone git clone git://github.com/Ardhat/avrdude-rpi.git</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>

In order that the Arduino IDE works properly with Ardhat, it needs to Reset Ardhat during code upload. It does that using the modified avrdude we just cloned, so enter the following commands:
<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Modify avrdude</p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">cd avrdude-rpi/</span>
        </p>        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo cp autoreset /usr/bin</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo cp avrdude-autoreset /usr/bin</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo mv /usr/bin/avrdude /usr/bin/avrdude-orig</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo ln -s /usr/bin/avrdude-autoreset /usr/bin/avrdude</span>
        </p>
        <p class="line">
          <span class="output"># => Now open the Arduino IDE and start programming Ardhat!</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>

Start the Arduino IDE
  



![image alt text](/media/ArdhatIDE.jpg)


And you're all set!!
