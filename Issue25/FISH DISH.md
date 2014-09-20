FISH DISH
A review of the Fish Dish circuit board

The Fish Dish (http://www.pi-supply.com/product/fish-dishraspberry-pi-led-buzzer-board) is a little circuit board, which is simple to build by yourself and ideal for children learning about the GPIO. Children please ask an adult to help with the soldering ¨C I accidentally melted part of the connector, but it still works fine!

The circuit board has three LEDs, one buzzer and a switch. There is a Python program available from the internet, but for children, Scratch is better. I only had normal Scratch on my Raspberry Pi, but it will not use the GPIO pins. I downloaded ScratchGPIO, as introduced in issue 9 and 10 of the MagPi and documented at http://cymplecy.wordpress.com/scratchgpio/scratchraspberrypi-gpio/ . This put a new Scratch on my desktop.

I could not copy the pin numbers from the Python program as they are different in Scratch GPIO and the allon command only turned on two LEDs and not the buzzer. I tried all the pins and worked out that if you turn them on then the allon command works. I made a simple program that turned all on and then all off when the button was pushed. I also ran a scratch program and the Python program at the same time, which was interesting as you can see what happens when two programs think they are controlling the same thing.

The right arrow code [1 ] adjusts the brightness of the red LED I connected to pin 13. It gets brighter then dimmer and then turns off. It will work for any LED and even for the buzzer, which can be very annoying if you do it for a long time. Just change the power13 to power7 for Green, power15 for Yellow and power21 for Red. The buzzer is on pin 24.

When green flag clicked [2] is a program that checks when the button is pressed on the Fish Dish. The button is on pin 26. It turns all the LEDs plus the Buzzer on when the button is pressed.

I used the up arrow key [5] to turn everything off and the space key [3] to turn the LEDs on and off. I also added a tricky code [4] to pin13off to confuse my brother.

There are also some left over pins to add extra LEDs and I later added a red LED and 1 k resistor on pin 13. The extra LED I put on pin 13 turns off when the button is pressed so I knew it worked.

If you add on a circuit to the pins that have the LEDs on then the LEDs tell you if your program works, so if your circuit does not work you can find the problem. I used a 1 k resistor for my external circuit and perhaps the resistors on the Fish Dish could be 1 k as well.

The Berryclip https://www.modmypi.com/berry-clip-raspberrypi- add-on-board?filter_name=berryclip is nearly the same as the Fish Dish, but you cannot add extra LEDs. However, it is ¡ê3 cheaper and it comes with more LEDs. I recommend the Fish Dish for children aged 6+, who are learning about Scratch GPIO, but it should cost less.