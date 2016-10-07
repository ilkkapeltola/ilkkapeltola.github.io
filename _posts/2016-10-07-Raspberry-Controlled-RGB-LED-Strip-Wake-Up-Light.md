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

The goal is to create a wake-up lamp that starts with a dim blue light perhaps 30 minutes before
wake-up and gradually increase to a warm white. I want to be able to configure it, ideally through a
web interface I can access at home on my phone. I'll settle for a console configuration first though.

Detailed instructions will come in here later :)

## Components

| Raspberry Pi Model B      | $35    |
| USB Wifi antenna          | $1.68  |
| RGB LED strip w/ power    | $9.67  |
| 12V to 5V power converter | $2.94  |
| IRLZ34N MOSFETs           | $2.95  |
| Breadboard                | $0.96  |
| Jumper wires              | $1.55  |
|                           |        |
| Total                     | $54.75 |

### USB Wifi Antenna - $1.68

So I already have a Raspberry Pi Model B, which is plenty for my need.

I wanted to have it connected to the WiFi, so I decided to order a small
<a href="https://www.aliexpress.com/item/Hot-Sale-Mini-PC-wifi-adapter-150M-USB-WiFi-antenna-Wireless-Computer-Network-Card-802-11n/32659894879.html">USB Wifi antenna 
from AliExpress</a> for it for $1.68.

<img src="/images/usb-wifi-antenna.jpg" width="200" />

### RGB Led strip and power supply - $9.67

I could power the Raspberry Pi and the LED strip separately, but I would need two power sockets.
We only have two power sockets in the bedroom, so I want to leave the other for e.g. mobile phone
charging. I want the light to be bright, so I went for the 60 LEDs per meter option with 12V.
According to <a href="https://learn.adafruit.com/rgb-led-strips/current-draw">the Interwebs</a>,
each 3-LED-segment draws 20mA from a 12V power suplly, so this would mean 2.4A max for a 2m long
strip (max). I indend to use the same supply for my 5V Raspberry Pi, so a 3A supply should suffice.

I ended up ordering <a href="https://www.aliexpress.com/item/Ultra-Bright-5M-5050-RGB-LED-Strip-Non-Waterproof-300-Led-Strip-Light-Flexible-Ribbon-Tape/32550636554.html">
this model</a>, which will also let me test out the strip before any other development and how it
will fit into the bedroom.

<img src="/images/rgb-led-strip.jpg" width="200" />

### 12V to 5V step down switch regulator - $2.94

I put a lot of research on this one. I learned that common linear regulators dissipate
heat like crazy, and I feel my bedroom is warm enough. I also learned that 'switch regulators'
should be more efficient. I found AliExpress to be quite conservative on the details on these.
Luckily, I found <a href="http://www.bajdi.com/testing-switch-mode-voltage-regulators/"> this</a>.
I searched for the KIM-055L models online and, although the description doesn't say that, I'm
confident <a href="https://www.aliexpress.com/item/24V-12V-To-5V-5A-DC-DC-Buck-Step-Down-Power-Supply-Module-Synchronous-Rectification-Power/32689938167.html">this</a> model is such.

<img src="/images/step-down.JPG" width="200" />

### MOSFETs - $2.95

Now, I didn't know what MOSFETs were. Turned out, they're like transistors i.e. you control
the high voltage (12V) going to the LEDs with lower voltage (~2.5V) coming from the Raspberry
GPIO ports. You need to do this as the GPIO ports will not have enough voltage or current to
drive the LEDs. Instead, we command the MOSFETs with the Raspberry to pass through the higher
voltage from the 12V source to the LEDs.

These [IRLZ34N MOSFETs](https://www.aliexpress.com/item/Free-shipping-5pcs-lot-IRLZ34N-30A-55V-IRLZ34NPBF-TO-220-new-original/32591803920.html)
- I THINK - should be pretty good fit for my needs. The threshold voltage is 1.0-2.0V, which
is less than what Raspberry can produce, meaning I should get the MOSFETs fully open (and
the lights fully brigh). Yet, they can handle up to 16V Gate-to-Source voltage, which to my
understanding of electronics should suffice. So I won't burn them, but they should be able
to provide all the power that's needed for the lights.

<img src="/images/mosfets.jpg" width="200" />

### Breadboard - $0.96

I need something to stick my MOSFETs etc into, so
[this](https://www.aliexpress.com/item/Free-Shipping-1pcs-DIY-400-Points-Solderless-Bread-Board-Breadboard-400-PCB-Test-Board-for-ATMEGA/32657614549.html)
seemed like a good option.

<img src="/images/breadboard.jpg" width="200" />

### Jumper cables - $1.55</h3>

And of course some
[jumper cables](https://www.aliexpress.com/item/Free-shipping-Dupont-line-120pcs-10cm-male-to-male-male-to-female-and-female-to-female/32376063784.html)
to connect things together.

<img src="/images/jumper-cables.jpg" width="200" />

### Profile for the LED - ?

I haven't decided on a profile for the LED strip yet. This will likely be the most expensive
part of this project - but also the most visible.

### Housing

Once I have everything else done, I plan to 3D print a housing for the Raspberry Pi and the
other components. I'll likely attach this to the underside of the shelf.

### Programming

I imagine I will be using CRON to command a <a href="https://pypi.python.org/pypi/RPi.GPIO">
RPi.GPIO</a> python script. Let's see how that develops.

### Now we wait

Components are being shipped as of 7.10.2016. Now we wait.