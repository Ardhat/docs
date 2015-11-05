---
title: Quick Start
weight: 30
toc: true
prev: 
current: quickstart
next: overview
---

Before connecting  to a host system such as Raspberry Pi, be sure to checkout the hardware setup instructions [here](/doc/configuration).

Once connected, you can power up the Ardhat, either from battery or using the DC barrel Jack on board, and the orange status LED will pulse.

To turn the Pi or compatible on, push the navigation switch, and the status LED will stay permanently illuminated.

At this point, Ardhat is ready to communicate over the [Firmata channel](doc/progmodel/), which requires some installation on the host, which is detailed [here](/doc/installation).

If you just want to program {{<ardhat>}} directly from Raspberry Pi, here's how to get the Arduino IDE up and running with Ardhat.

<section class="quickstart" >
  <div class="grid">
    <div class="unit .half code">
      <p class="title">Quick-start Instructions</p>
      <div class="shell">
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">git clone git@github.com:Ardhat/avrdude-rpi.git</span>
        </p>        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">cp autoreset /usr/bin</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">cp avrdude-autoreset /usr/bin</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">mv /usr/bin/avrdude /usr/bin/avrdude-orig</span>
        </p>
        <p class="line">
          <span class="path">~</span>
          <span class="prompt">$</span>
          <span class="command">ln -s /usr/bin/avrdude-autoreset /usr/bin/avrdude</span>
        </p>
        <p class="line">
          <span class="output"># => Now open the Arduino IDE and start programming Ardhat!</span>
        </p>
      </div>
    </div>
    <div class="clear"></div>
  </div>
</section>



