---
layout: post
title: Raspberry Pi Controlled RGB LED Strip Wake-Up Lamp
---

For a long time I've wanted a wake-up lamp. In our new appartment, there simply
isn't room for a traditional one. I'm sure there would be some commercial alternatives
for me, but I just felt like doing something with my Raspberry Pi.

![_config.yml]({{ site.baseurl }}/images/bed-shelf.jpg)

So I embarked on a journey to make a Raspberry Pi controlled RGB LED strip wake-up lamp
that would fit on the shelf. I'm going to build this cheap, but with some degree of quality (hopefully)

Detailed instructions will come in here later :)

<h2>Components</h2>

<h3>USB Wifi Antenna - $1.68</h3>

So I already have a Raspberry Pi Model B, which is plenty for my need.

I wanted to have it connected to the WiFi, so I decided to order a small
<a href="https://www.aliexpress.com/item/Hot-Sale-Mini-PC-wifi-adapter-150M-USB-WiFi-antenna-Wireless-Computer-Network-Card-802-11n/32659894879.html">USB Wifi antenna 
from AliExpress</a> for it for $1.68.

![_config.yml]({{ site.baseurl }}/images/usb-wifi-antenna.jpg)

<h3>RGB Led strip and power supply</h3>

I could power the Raspberry Pi and the LED strip separately, but I would need two power sockets.
We only have two power sockets in the bedroom, so I want to leave the other for e.g. mobile phone
charging. I want the light to be bright, so I went for the 60 LEDs per meter option with 12V.
According to <a href="https://learn.adafruit.com/rgb-led-strips/current-draw">the Interwebs</a>,
each 3-LED-segment draws 20mA from a 12V power suplly, so this would mean 2.4A max for a 2m long
strip (max). I indend to use the same supply for my 5V Raspberry Pi, so a 3A supply should suffice.

![_config.yml]({{ site.baseurl }}/images/rgb-led-strip.jpg)

<h3>12V to 5V step down switch regulator<h3>


