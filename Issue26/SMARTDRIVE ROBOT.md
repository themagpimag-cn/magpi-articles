SMARTDRIVE ROBOT
Coding a remote-controlled robot with the SmartDrive add-on board

How to control a robot with a joystick

The Raspberry Pi is amazing in the sense that it can be used to create programs for almost any purpose. I 've seen people create media centres, cloud storage devices, weather stations, video game emulators and various other implementations on this little computer.

However, I wanted to start off with something that didn't require lots of software maintenance and decided upon creating a remote-controlled robot. The hardware specifics of this robot will vary from user to user, therefore I want to focus on the coding required to get the robot to move.

I use a joystick to control my robot. To control the motors I use a SmartDrive controller. This is a motor driver that allows you to control up to two high current motors with the Raspberry Pi.

When starting this program, it is important to import the following modules:

The pygame module is used to create a joystick object, the sys module is to be able to quit the program when prompted and the os module is to read the string environment.

This is the code to create the joystick object:

A try-except block is recommended because it is important to be able to catch the exception of a pygame. error for debugging purposes.

When creating the code to actually move the robot, it is helpful to create a separate function for that purpose.

The function is as follows:

When the direction is 0, the motor will run backwards and when the direction is 1 , the motor will run forwards. The SmartDrive speed ranges from 0-1 00 therefore it is important to keep within this scale. This function can now be called whenever prompted.

When starting on the main loop of the program, please note that scaling for the joystick axis is required. The get_axis function from pygame ranges from -1 to 1 , with 0 being centered. Therefore we need to scale by 1 00 to be able to use the axis values for the speed parameter in the above move function. The main loop code is as follows:

The get_button function is used to quit the program and stop the robot from running.

I have listed all of the electrical parts, motors and other hardware that I have used for this project. I would also recommend checking out your local scrapyard for any motors that you would like to use instead of buying them. My recommendation would be to look for window motors, or electric toy car motors. I decided to use the SmartDrive because it is capable of supporting up to 300W per motor, though I only used motors that ran at 22W each! There is definitely more headroom to use the SmartDrive for more serious projects.

As mentioned previously, the SmartDrive allows the Raspberry Pi to control up to two high current motors. The SmartDrive is controlled by the Raspberry Pi using the I2C interface.

The programming interface (API ) is coded in Python and contains various different functions that allow you to control the motors in a variety of different ways. Two motors can be connected to the SmartDrive the two black screw terminals labeled M1 and M2. (The third black screw terminal is for power.) I t is also possible to program the SmartDrive with the C language.

There are functions that allow you to run the motor in terms of degrees turned, time run in seconds and even for a certain number of rotations. I t also supports rotary encoders. A nice bonus feature of the SmartDrive is that it is capable of providing a 5V output which can be used to power the Raspberry Pi without using another power source.

Parts List:
1 . SmartDrive:
http://www.openelectrons.com/pages/34
2. Tempest TR1 .3-1 2 Battery (1 2V):
http://www.tempestbatteries.com/html/tr1.3-12.html
3. DreamGrear Shadow USB wireless joystick:
http://www.dreamgear.net/shadow-6-wirelesscontroller-for-ps3-1.html
4. 2x Pittman GM9234E765-R1 motors:
http://www.gearseds.com/competition_motor.html