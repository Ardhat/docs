---
title: Quick Start
prev: /doc/
next: /doc/installation
weight: 30
toc: true
---


For the impatient, here's how to get the Arduino IDE up and running with Ardhat. More detailed instructions [here](/doc/installation).

   
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



