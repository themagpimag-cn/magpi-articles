PIBOT
Part 1 : Learn the fundamentals of robotics

Give your Raspberry Pi robot powers
Learn the fundamentals of robotics - Part 1

Introduction

The robot revolution is coming. Robots are no longer just machines from science fiction. From self-driving cars, to flying drones, robots are on the march. Over the next few years robots are going to be seen all over the place and will be increasingly used in agriculture, manufacture, medicine and education, as well as in our own homes. The amazing thing is that now almost anyone can become a roboticist and if you have a Raspberry Pi you are already half way there.

In the first part of this two part article, I will give you an introduction to the exciting new world of robotics and will detail all the things you need to consider when embarking on building your own robot. As an example we will cover the building of the simplest robot possible for the Raspberry Pi. Next time, in part 2 of the article, I will cover more advanced robots and show how you can build and then program these robots to do some really interesting things.

Before we get into the what and how-to of any robotics, the first question may be why would you want to build a robot with a Raspberry Pi in the first place? Also, what kind of things will a Raspberry Pi robot be able to do?

I first got interested in Raspberry Pi robots when I realised how good they can be for learning about technology and also the teaching of technology to others. The great thing about robots is that they are physical and immersive. Instead of providing output to pixels on a screen, a robot is in your personal space and its movements, lights and sounds go way beyond the limits of a screen. With the Raspberry Pi and some low cost hardware, not only can you make a robot move, you can make a robot that can speak, dance and a whole lot more besides! Why wouldn't you want to turn a Raspberry Pi into a robot?

What makes the Raspberry Pi so good for robotics (as well as so many other projects) is its special GPIO port (General Purpose Input Output). This allows the Raspberry Pi to connect to all kinds of electronics and hardware. The fundamental requirements for the most interesting robots are the ability to both sense and interact with their environment, and it is the GPIO port of the Raspberry Pi that makes this possible.

Before going into further details for building a simple robot, let's first consider some robot fundamentals.

What makes a robot robotic?

Wikipedia defines a robot as "a machine which can be electronically programmed to carry out a variety of physical tasks or actions". In addition to this requirement to perform physical actions, a proper robot should also have an autonomous ability. Autonomy allows a robot to act independently in the world and this makes them different from things like radio controlled vehicles that are not able to function by themselves. The Raspberry Pi's processing ability (both CPU and GPU), along with its GPIO port, gives it lots of potential for developing autonomous behaviour. As a simple example let's take a look at the classic line following robot.

A line following robot has the ability to move forward, change direction and detect a line on the ground. This is a classic example of autonomous behaviour. No matter where the line leads, the robot is programmed to follow the line without the need for any external control.

For our simple robot we are going to add an infrared (IR) sensor that detects a change in reflectivity. The reflectivity of the ground changes when the robot moves off the line. When this happens it changes direction to get back on the line.

[pic]

While autonomous behavior can be very useful in a robot it can also be a lot of fun to control it directly. Some of the most interesting applications happen when a robot combines the two. Imagine a flying robot that can fly around at your command but can also be programmed never to crash into walls and other obstacles.

Anatomy of a Raspberry Pi robot

Let us go through all the things you need to build your own robot using a Raspberry Pi. I will detail a minimal possible Raspberry Pi robot step by step. These basic steps are:

? Remote access to the Raspberry Pi
? Powering a Raspberry Pi without cables
? Building a robot chassis
? Making the robot move
? Adding sensors

The first hurdle to turning a Raspberry Pi into a robot is to untether it from all wires and cables.

Remote access

Most people will be familiar with interfacing a Raspberry Pi to a monitor/TV, keyboard and mouse, but this is just not going to work for a robot. The best thing for connecting remotely is a wireless dongle connected to the Raspberry Pi USB port. I won't go into all the details for doing this here. Instead, visit http://pihw.wordpress.com/guides/guide-to-remoteconnections/.

Another interesting thing to note is that you can either connect wirelessly across an existing network or you could turn your Raspberry Pi into a wireless hotspot and connect to it via its own network. See Issue 1 1 of The MagPi, page 1 0 (http://www.themagpi.com/issue /issue1 1 /article/turn-your-raspberry-pi-into-a-wireless -access-point) for details.

Rather than using the Raspbian Desktop on the robot, a terminal interface is more suitable. When communicating across the wireless network, a remote SSH terminal session is the best way to send commands. Details are in the previously mentioned guide to remote connections.

Portable robot power

The next essential for the robot is to get the Raspberry Pi running on portable electrical power. The simplist way to do this is to use a backup USB mobile phone charger. Personally I opted for a basic 4 x AA battery pack with a 5V voltage regulator. I f you are using a Model B then a 8 x AA battery pack may be preferable to get longer running time.

Building a robot chassis

While it is possible to use some kind of existing chassis to build your robot, it can also be fun to make your own. Even some stiff cardboard can be used for this. The photo overleaf shows a basic design.

[pic]

Making the robotmove

Now that you have successfully untethered your Raspberry Pi and can connect to it remotely, we can give it some robot powers - motion! The simplest and probably cheapest way to give your robot motion is by connecting two continuous rotation servos.

Normally servos are designed to turn just 90 or 1 80 degrees though modified versions exist that provide continuous rotation to be able to drive wheels. Adafruit show how to modify a low cost servo for continuous rotation (http://learn.adafruit.com/ modifying-servos-for-continuous-rotation). I f you want to be really inventive you can also make your own wheels. In the photo above, two large bottle tops are being used for wheels.

With two wheels to drive the robot a third wheel is usually required for support. I t is positioned in the middle towards the back of the chassis. Ball bearing castors or furniture wheels can work well but to keep things really simple a smooth sliding support can be made using a paperclip.

Now that the robot has wheels the next important step is to connect the servos to the GPIO port. As a hack I made up a simple circuit. This connects the data pins of the servos and the IR sensor to the GPIO and also connects the positive and negative power pins of the servo to a 5V voltage regulator. The circuit is shown on the right.

[pic]

Making your robot sensational

To keep things simple we will only add an IR sensor to our robot. The way this works is that it has one LED that is an IR emitter and one that is an IR receiver. The receiver measures the light reflected from the ground and the amount received will depend of the reflectivity of the surface. A line that has a different reflectivity to the ground around it can be measured by the sensor so it knows whether it is on or off the line.

[pic]

A suitable sensor can be obtained from http://www.banggood.com (search for LM393 IR).

Coding autonomous behaviour

Now that we have the hardware of the robot sorted, it is time for the code. The Python script shown on the next page is all that is required to add both remote control and autonomous line-following behaviour to our robot. A detailed explanation of the code is available at http://www.pibot.org/tiddlybot/code.

Beyond the basics

Next month we will look at some more capable robots with features like speech, voice recognition and environment mapping. We will also discuss adding more hardware via an Arduino interface.

In this first part I hope you've become more familiar with the basics of building a robot and hope you agree that building robots with the Raspberry Pi is affordable and fun.

To help make it easier for Raspberry Pi users to get into building robots I have now developed the "TiddlyBot". This brings the ideas described in this article to an easier "build-your-own" robot kit. For "TiddlyBot" I have also added some exciting software as well as things like line drawing capabilities. To find out more and to support the "TiddlyBot" project, please see our Kickstarter (http://kck.st/1pOgU1J) until 26 July 2014.

With the Raspberry Pi anyone can now be a roboticist and I hope this helps people to both learn and have fun!