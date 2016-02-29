---
title: Installation
weight: 30
toc: true
prev: expansion
current: installation
next: power
---


Getting {{<ardhat>}} installed and ready-to-go should only take a few minutes.

The [Optiboot](/doc/upgrading) bootloader is already installed on {{<ardhat>}}'s processor, but we need to make sure the Raspberry Pi is setup correctly, and has the necessary software in place.  

The easiest way to do this is from the command line, and the best way to do that, is to ssh into the Raspberry Pi so that you can copy and paste the commands below into your terminal (you can use [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) if you are not on a Unix based system like Linux or OS X).

By default, Raspberry Pi copies its shell and kernel messages to the serial port. As {{<ardhat>}} uses this channel to communicate with the host, we need to disable that. This is most easily done with the in-built utility [raspi-config](https://www.raspberrypi.org/documentation/configuration/raspi-config.md).


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

From the menu, select `Advanced Options`

<br>
![image alt text](/media/raspi-config.png)
<br>  
Then select `Serial`

<br>
![image alt text](/media/raspi-config-serial.png)

<br>
and disable shell and kernel messages on serial

<br>
![image alt text](/media/raspi-config-serial-no.png)

<br>
Back at the `Advanced Options` menu you'll also want to enable I2C, so that you can access the {{<ardhat>}} peripherals directly if required

<br>
![image alt text](/media/raspi-config-I2C.png)  

<br>
Enable both the `ARM I2C interface` ...  
<br>  

![image alt text](/media/i2c-en.png)

<br>
...and the loading of kernel modules  
<br>  

![image alt text](/media/i2c-kernel.png)

<br>Now we need to load a few software pre-requisites...  

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
          <span class="command">sudo aptitude install git arduino i2c-tools</span>
        </p>        
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">git clone git://github.com/Ardhat/avrdude-rpi.git</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>



In order for the Arduino IDE to work properly with {{<ardhat>}}, it needs to perform a reset during code upload. It does this using the modified avrdude we just cloned, so enter the following commands:  

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
          <span class="command">sudo mv /usr/bin/avrdude /usr/bin/avrdude-original</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo ln -s /usr/bin/avrdude-autoreset /usr/bin/avrdude</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>


Finally, so that the Arduino IDE can 'see' the {{<ardhat>}} serial port, we need to create a symlink between the Raspberry Pi ttyAMA0 port and ttyS0.


<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Create a link to ttyS0  </p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">sudo -i</span>
        </p>        
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">#</span>
          <span class="command">echo 'KERNEL=="ttyAMA0", SYMLINK+="ttyS0",GROUP="dialout",MODE:=0666' >  /etc/udev/rules.d/80-ardhat.rules</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">#</span>
          <span class="command">udevadm trigger</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>


Start the Arduino IDE...




![image alt text](/media/ArdhatIDE.jpg)


...and you're all set!!
