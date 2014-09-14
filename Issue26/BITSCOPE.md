BITSCOPE
Part 2: Electronic measurement with the BitScope oscilloscope add-on board

In last months article, we equipped the Raspberry Pi with a BitScope Micro add-on board and installed the BitScope digital storage oscilloscope (DSO) software. Now we are ready to delve into the fascinating field of electronic measurement with a fully-fledged DSO.

In Part 1 you learnt that an oscilloscope measures electrical voltages. So let¡¯s start by measuring the voltage of the Raspberry Pi itself.

Identify the channel control pad for Channel A (7) and set it to 2V per Div. This means that one square of the y-axis on the main screen represents 2V. With 8 squares stacked up on the Y-axis we are able to measure a maximum of 1 6V. Now connect the red test lead to pin CHA and the black test lead to pin GND, opposite pin CHA on the BitScope Micro. Fig. 2 shows the pin layout of the BitScope Micro to help you to select the right pins.

Press the top of the black test lead down, so that the metal gripper appears at the opposite side and connect to pin 6 of the GPIO on the Raspberry Pi. Do the same with the red test lead but connect it to pin 2 of the GPIO. Fig. 3 shows the setup.

Look at the main screen of the BitScope DSO (1 ). The x-axis is the line in the middle and has small vertical lines to sub-divide each square. This is our 0V line. But our yellow beam is in the middle of the third square above the x-axis. Because we know there is a voltage of 5V between pin 2 (the plus pole) and pin 6 (the minus pole), and we set the channel control to 2V per Div, so the horizontal line indicates exactly this voltage. In Fig. 4 I have inserted an extra scale in red on the y-axis to help you interpret the screen.

You may get a reference measurement with your multimeter, if you like. Could we measure other and higher voltages than 5V? Sure, but what about our input range? We have to change the input range with the channel control for Channel A (7) to an appropriate value. While working with an oscilloscope you should always be aware about the settings of the instrument and the expected voltages in the circuit.

Is this NE555 timer IC still working?

In our next experiment we want to find out if a NE555 timer IC is still functional. This IC is often used when a clock signal is required. For this experiment we need:

? 2x 1 K resistors (R1 , R2)
? 0.1 CF capacitor (C1 )
? 1 0 nF capacitor (C2)
? NE555 timer IC (IC1 )
? small breadboard
? test leads provided with the BitScope Micro

Fig. 5 shows the circuit diagram and Fig.6 shows you how to implement this circuit on a breadboard.

When you have finished building the clock generator on the breadboard, set the time base control (6) to 50 Csec per Div and the channel control pad for Channel A (7) to 2V per Div. Additionally, set the trigger controls (4) to MEAN.

Our Raspberry Pi has enough power to supply the +5V the clock generator needs. Therefore connect a blue test lead from pin 6 of the Raspberry Pi GPIO (Gnd) to the Gnd connection of the breadboard and a green test lead from pin 2 of the Raspberry Pi GPIO (+5V) to the Vcc connection of the breadboard.

Two more test lead connections are needed. Connect pin 3 of the NE555 with CHA of the BitScope Micro and connect Gnd of the breadboard with Gnd of the BitScope Micro, opposite CHA.

Phew! Things can get complicated fast. Look at Fig. 7 and make sure you have all the connections right.

Fig. 7: Connecting the clock generator to the Raspberry Pi and BitScope Micro

Look at the main screen of the BitScope DSO software (1 ) and you should see a similar square wave, as shown in Fig. 8.

Fig. 8: Output of the clock generator circuit

This square wave proves that our NE555 is still functional and could be used for our next electronics project. I f you do not see a square wave, check your circuit for any errors. I f all connections between the different parts and the Raspberry Pi are ok and you still don¡¯t get a square wave it can be assumed that the NE555, or one of the other components, is defective.

If your clock generator is operational you may try to find out the frequency with which your clock generator is running. For the answer you should look at Fig. 8 (or the measurement on your own screen) and remember what I wrote about measuring frequencies in Part 1 last month. As an aid, I have drawn a line in red on the output diagram showing that the period of the square wave is 200 Csec.

In this second part we measured voltage and frequency. In the next part there will be some more experiments with the clock generator and how to put an oscilloscope to good use.

The BitScope Micro add-on board is available from BitScope Designs in Australia (http://www.bitscope.com), in Germany from BUTTE publishing company (http://www.butteverlag.de), in the UK from Pimoroni (http://shop.pimoroni.com) and in Switzerland from (http://www.pi-shop.ch). A German translation of this article is available at http://www.butte-verlag.de.