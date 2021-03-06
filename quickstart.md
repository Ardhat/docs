---
title: Quick Start
weight: 30
toc: true
prev: configuration
current: quickstart
next: installation
---

Before connecting  to a host system such as Raspberry Pi, be sure to checkout the hardware setup instructions [here](/doc/configuration).

Once connected, you can power up {{<ardhat>}}, either from battery or using the onboard [DC barrel Jack](/doc/power) , and the orange status LED will pulse.

To turn the Pi or compatible on, push the navigation switch, and the status LED will stay permanently illuminated.

At this point, {{<ardhat>}} is ready to communicate over the Firmata channel. For more info on which host apps to use, see [here](/doc/progmodel).  

If you want to program {{<ardhat>}} directly from Raspberry Pi, there are full instructions [here](/doc/installation), but for the impatient, here's the quick way to get the Arduino IDE up and running with {{<ardhat>}}.

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
