BITSCOPE
An oscilloscope add-on board for the Raspberry Pi

OSCILLOSCOPE
Electronic Measurement? BitScope & RasPi!

An oscilloscope is only for professionals and rather expensive!? I f you think this sentence is true then read on.

The BitScope Micro from the Australian manufacturer BitScope Designs is a small addon board especially adapted to the Raspberry Pi, with which you can turn your Raspberry Pi into an oscilloscope, logic analyser, spectrum analyser and a waveform generator. In this miniseries, I am going to show you how to setup this dynamic duo and use its features to understand how electronic circuits work and debug them if they do not work.

First things first: what is an oscilloscope anyway? An oscilloscope is an electronic measurement device with which you can measure different electrical parameters such as voltages, frequencies, etc.. With a digital multimeter you are able to measure an electrical voltage and see a numerical representation of it in the display. However, an oscilloscope presents a graphical representation of the voltage over time. The oscilloscope does this by plotting measurements using a Cartesian co-ordinate system.

In this first part of the article we are going to setup the hardware, install the software and take our first graph.

Assuming you have your Raspberry Pi up and running, make sure that your Raspbian installation is up to date by typing:

Next, install the BitScope software with the following procedure:

1 ) Download the BitScope DSO 2.7 package from the BitScope Download area from http://bitscope.com/pi/and save it into the directory/home/pi on your Raspberry Pi.

2) When the download is complete, fire up your file manager, navigate to /home/pi directory and right click on the downloaded package and choose Open with from the context menu.

3) Select the custom command line tab, enter sudo dpkg -i and click OK.

4) When the installation procedure has finished, connect the BitScope Micros USB port to the Raspberry Pi as shown in Fig. 1 . You will need a powered USB hub to do so, because normally both USB ports of the Raspberry Pi are in use for the keyboard and the mouse.

Figure 1: Connecting the BitScope Micro to your Raspberry Pi via USB

5) You should be able to start BitScope DSO from the main menu now and see its splash screen on your monitor. With your BitScope Micro connected click POWER on the right side of the splash screen.

With BitScope DSO up and running and the BitScope Micro add-on board connected, the only thing left before we start exploring the system is to familiarise ourselves with the user interface on the screen. Fig. 2 shows the main screen.

In the main display (1 ) you will see the results of the measurements in graphical form. This output is dependent on which buttons you choose on the right side (2). When measurements are taken is very important if you are working with an oscilloscope. Electronic engineers talk about triggering. (3) is called the trigger window, which we will leave at the default automatic mode for the moment. We will change the trigger behaviour with the trigger controls (4) at a later time. For exact measurements, BitScope Micro supports us with so called cursor measurements (5). With the time base control (6), we are able to zoom in and out of a graph and therefore see more or less details. The channel controls (7) let us influence the input, its source, range, vertical position and scaling. Last but not least the capture control (8) defines the capture sample rate, duration, frame rate and display modes.

Figure 2: BitScope DSO software main screen elements (photo courtesy by BitScope Designs)

First measurement

To check if your setup is ok and working, connect one of the test leads, which are included with the BitScope Micro, to the channel A pin (marked CHA (yellow), see Fig. 3):

Figure 3: Pin layout of the BitScope Micro (photo courtesy by BitScope Designs)

Next change the time base (6) to 5msec/Div by clicking on the left arrow key until this value is displayed. 5msec/Division means that each square of the grid on the main screen (1 ) on the x-axis represents five milliseconds. Next look at the channel controls for channel A (7) and select 1 V/Div. This means that each square of the grid on the main screen (1 ) on the y-axis represents one volt. Now press down the top of the grabber clip, such that you can see the tiny metal grabber coming out of the plastic on the opposite side and touch it with your finger. Do not be afraid nothing will happen, except if you let loose the top, then it will bite you. I f you look to the main screen you will see a more or less perfect sine wave like the one in Fig. 4:

Figure 4: Touching the test lead with your fingertip

Where does this sine wave is come from? Take your finger from the metal grabber and it will disappear. Put it on again and the sine wave will reappear. No doubt, you are the source of the mysterious sine wave. How? Mains electricity is provided at each power outlet and has an alternating current with a frequency of 50 Hz (in Europe and 60 Hz in the USA). A wire that carries an alternating current behaves as a radio transmitter. Your body is receiving the signals from the transmitting wire. When you touch the metal grabber, the signal is transmitted to the BitScope Micro oscilloscope and onto the Raspberry Pi screen. Why am I so sure that the sine wave displayed has a frequency of 50 Hz? Well, look at Fig. 5:

Figure 5: Determining the frequency of a signal

We selected 5msec/Div, where one cycle of the signal is 4 divisions long. 5msec*4 equals 20 msec (or 0.02 seconds. Since an oscilloscope cannot measure frequencies directly, we have to take the reciprocal of 0.02 seconds which is 50 Hz.

In this article we discussed what an oscilloscope is all about, set up the hardware and software, and checked the whole setup by injecting a 50 Hz sine wave with our fingertip.

Join me next month, when we start to delve into the fascinating field of electronic measurement with a digital storage oscilloscope. Yes, that is what our BitScope Micro is. For all those interested in actually turning their Raspberry Pi into a digital storage oscilloscope with the BitScope Micro add-on board, it is available from BitScope Designs in Australia (http://www.bitscope.com). In Germany, it is offered by BUTTE publishing company (http://www.BUTTE-verlag.de). In the UK, you can order the BitScope Micro at http://shop.pimoroni.com and in Switzerland at http://www.pi-shop.ch. A German translation of this article is available at http://www.BUTTE-verlag.de/.