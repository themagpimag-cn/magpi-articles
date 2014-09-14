PI CANVAS DIGITAL ART DISPLAY

How to display dynamic art using a Raspberry Pi

In the past digital artists have been limited to static images (prints) when creating wall art. The Pi Canvas allows digital art to be created and displayed on a wall just like a framed print. However, the art is now dynamic which opens up new creative opportunities.

In this article I will describe how you can make a Pi Canvas using your Raspberry Pi to produce a display of dynamic art - art which can optionally interact with viewers.

What is Pi Canvas?

Pi Canvas is a Raspberry Pi mounted on an HDTV that has a USB connector to power the Raspberry Pi. The Pi Canvas has no keyboard, no mouse, nor does it respond to the TV remote control. I t is simple to use. Just hang it on the wall, plug it in, press the power button and let it do its thing.

The Pi Canvas can operate 24/7 or be powered on and off as required. I t can also be made to interact with its environment through electronic sensors (e.g. ultrasonic or infrared) which opens up even more creative opportunities.

How to make a Pi Canvas?

The hardware and software used are all popular, open source and well documented. Basic knowledge of the hardware and software is not covered here as there are many excellent tutorials available online. The Pi Canvas was developed in the Faulhaber Fab Lab at the Suncoast Science Center in Sarasota, Florida. I t supports STEAM education (Science + Technology + Engineering + Art + Mathematics) for all ages. For more details, please visit http://www.suncoastscience.org.

Pi Canvas hardware

The Pi Canvas hardware requirements are simple:
Raspberry Pi (model A or B)
USB <-> micro USB cable (for power)
HDMI male to male coupler
HDTV (e.g. VIZIO model E390-A1 )

While any HDTV can be used, the example HDTV is particularly good as it has a USB connector sufficient for powering the Raspberry Pi. I t also has a recessed area on the back for attaching the Raspberry Pi, which allows for flush wall mounting. Finally it has a narrow, clean bezel which makes a nice frame.

Pi Canvas software

Just like the hardware, the Pi Canvas software requirements are simple and familiar to many:

Latest Raspbian OS
Chromium web browser
HTML5 Canvas element
JavaScript

Chromium has a kiosk mode for full screen operation with no browser decoration or controls. The HTML5 Canvas element offers good graphics capabilities for art and is fast. Finally JavaScript is an easy but capable language for browsers. This software combination runs very well on a Raspberry Pi.

Example JavaScript tutorials can be found at http://www.w3schools.com/js/. You should also visit http://www.html5canvastutorials.com.

Pi Canvas configuration

In addition to the normal Raspberry Pi setup, the following steps are required to make a Pi Canvas with the listed hardware and software. You will need separate power for the Raspberry Pi because the HDTV does not supply adequate power for this step.

Enter the following on the command line:

When the Raspberry Pi Software Configuration Tool appears, enable the option to boot to desktop.

Next we will install the chromium package plus some other utilities. The unclutter package removes the mouse cursor from the screen after some inactivity.

Your dynamic artwork is a web page. On the next page there is some example artwork code. Enter this code into a text editor and save it as sample. html. Put this sample file into the /home/pi/ folder.

When the Raspberry Pi is powered on, we want to automatically start Chromium with the artwork running. On the command line enter:

Comment out the following lines by prefixing them with a #:

Then add the following lines:

In nano you should see the following:

To save your changes press <Ctrl>+X, then Y then <Enter>.

When you restart your Raspberry Pi, the sample artwork should automatically appear. To open a second login press <Ctrl>+<Alt>+F2. To return back to the art display press <Ctrl>+<Alt>+F7.

Pi Canvas artwork

The Suncoast Science Center has a display area for showcasing inventions of all kinds created in the Fab Lab. Here is a screen shot of a Pi Canvas on display in the Fab Lab display area. The artwork is titled "Loose Weave Digital Fabric". In April it won an award at the Art Center Sarasota ¡°One World¡± exhibition.

The artwork creates a new digital fabric every ten minutes. Drawing the digital fabric is an important visual aspect of the artwork and takes about five minutes.

The fabric colour is random and the thread colours are random within +/- 45 degrees of the fabric colour on the HSLA (Hue - Saturation - Lightness - Alpha) colour wheel.

Pi Canvas sample artwork code

Here is a sample artwork file which draws a "starburst" approximately every 1 0 seconds. The hues remain within 30 degrees of the initial, random hue on the HSLA colour wheel.

What happens if you change the values of dhue or tension?