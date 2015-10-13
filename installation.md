---
title: Installation
weight: 30
toc: true
prev: expansion
current: installation
next: progmodel
---


Getting Ardhat installed and ready-to-go should only take a few minutes.

The Optiboot bootloader is already installed on {{<ardhat>}}'s processor, but avrdude needs to be modified to work with Raspberry Pi hardware. 




There are a few pre-requisites, which are best installed from the command line, and the best way to do that is to ssh into the Raspberry Pi Linux instance, so that you can copy and paste the commands below into your terminal

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

Then install some essential packages

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

Setup the Arduino IDE to work with Ardhat

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
