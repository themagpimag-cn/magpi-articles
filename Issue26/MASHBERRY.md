MASHBERRY
Homebrewing with the Raspberry Pi

Introduction

When you are into homebrewing, you are faced with different problems. Brewing equipment, preferably, should be low priced. When doing allgrain brewing, there is also the need for a system that can control the temperature of the mash at different points and at different times.

There are professional brewing controllers available, but these are very expensive. So the idea was to build a cheap brewing-controller mainly from standard components. The controller should have a graphic display, a web interface for configuration and a recipe management system to make brewing different sorts of beer easier. The Raspberry Pi seemed to be ideal.

Brewing beer

Beer is made from malt, hops, water and yeast. To get a beer out of these ingredients, several processing steps are needed. These steps are in general:

Mashing
Lautering
Hop boiling
Fermentation

The first step in brewing is the mashing. During this step the starch of the malt is converted to sugar and extracted from the malt so the wort is obtained. (Wort is the liquid extracted from the mashing process during the brewing of beer.)

The conversion of the starch to sugar is done by the enzymes contained in the malt. To optimise the conversion to sugar by the enzymes, multiple resting periods at different temperatures are needed. These temperatures have to be held for specific times. That's the point where MashBerry is used.

After mashing, the malt is separated from the wort in a process called lautering. I t is basically a kind of filtering. After the lautering, the wort is boiled with hops. In this step, the beer gets hop flavours and bitterness.

Additionally, some chemical processes take place while boiling. These processes, for example, will clean the wort from the proteins. After boiling, the wort is cooled down and yeast is added to ferment the beer (in this step, the yeast is producing the alcohol).

After fermentation the beer is bottled and aged for several weeks or months, depending on the type of beer. Then it's ready to drink.

Hardware

To use a Raspberry Pi as a brewing controller, two main interfaces had to be added. The first interface is a temperature sensor for measuring the temperature of the mash. There are two possibilities for temperature sensors: a cheap DS1 820 sensor or a more accurate PT1 000 sensor with a Hygrosens I2C converter module.

The Hygrosens module (THMOD-I2C-R2) is a small module with an I2C interface that directly converts the value read from a PT1 000 sensor to a usable temperature. To use this converter an I2C level shifter between 5V and 3V3 is needed to connect it to the Raspberry Pi.

As an alternative, a DS1 820 sensor can be used. There are sensors with the appropriate metal housing and temperature range (>1 00°„C) available. These sensors can be connected to the Raspberry Pi using only a single resistor.

To control the electric heater of the mash container, a solid state relay (SSR) is used. The SSR is driven by a simple transistor circuit connected to the GPIO of the Raspberry Pi. Such a circuit also drives the piezo beeper. The SSR is housed in an external box including power plugs and filters.

For visualization a 3" TFT display is connected to the Raspberry Pi's composite video port. An IR receiver can be connected to the GPIO to enable MashBerry to receive IR codes from a common IR remote control.

Software

The MashBerry software is built using the Qt framework. The heart of it is the PID controller, which is used to control the temperature of the mash. The PID controller uses the temperatures of the temperature sensor as an input and outputs a power value between 0-1 00%.

A PID controller is a controller with a feedback loop. Each time the PID algorithm is triggered the temperature error between the set point and the actual temperature is calculated.

With this error, the old output value and the PID parameters (Kp, Ki, Kd), a new output value is calculated using the three values called the proportion, the integral and the derivative (PID).

The PID controller has the advantage (if properly tuned) to reach a nearly constant temperature.

The power value from the PID is then fed into a kernel driver which controls the GPIO in realtime. This driver is basically a hack of the system's timer interrupt, where the switching of the GPIO takes place.

The driver does the switching from 0-1 00% in two seconds. One percent of output power results in 20ms of on-time for the SSR. At 50Hz mains frequency this is one AC cycle per percent. With this method the power of the heater can be controlled very accurately.

The PID parameters can also be autotuned.

More info about PID controllers can be found at http://en.wikipedia.org/wiki/PID_controller.

The MashBerry application runs on a Linux system without X1 1 , using the embedded version of Qt4 which runs directly on the framebuffer. So very little resources are used.

The software can be downloaded from http://sebastian-duell.de/en/mashberry/downloads.html

There is also a complete SD card image available. It is based on Raspbian and includes the MashBerry application, the framebuffer version of the Qt libraries and a modified Linux kernel, which is capable of driving the SSR relay via the GPIO in real-time.

Building a MashBerry

To build a MashBerry you need the following parts:

 Raspberry Pi and SD card
 Power supply with 5V and 1 2V
 Housing
 2x BC547B transistor
 2x 1 50R resistor
 2x 1 00K resistor
 3x 1 K5 resistor
 DS1 8B20 temperature sensor
 1 2V Piezo beeper
 26-pin header for Raspberry Pi connector
 Solid state relay suitable for your power needs
 
Optional:

 TSOP31 236 IR-receiver
 3" TFT Display
 
Reference

Helpful information on the beer brewing process can be found at http://www.brewwiki.com.

Brewing is the production of beer through the fermentation of extracts from malted grains - traditionally barley or wheat. Malted grains are made by allowing grains to germinate and then drying them in kilns. The malting process develops enzymes necessary for converting complex starches into sugars.

Mashing is a step in the brewing process that combines crushed malts with hot water in a mash tun to convert complex starches into simple sugars that are more readily fermented. There are many variations of mashing, but the single infusion mash is easily done with home equipment and suitable for most popular beer styles.

Lautering is a process in brewing beer in which the mash is separated into the clear liquid wort and the residual grain. Lautering usually consistsof 3 steps: mashout, recirculation and sparging.