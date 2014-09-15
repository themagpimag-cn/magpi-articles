## SMARTDRIVE ROBOT
## SMARTDRIVE机器人

### Coding a remote-controlled robot with the SmartDrive add-on board
### 使用 SmartDrive 扩展板编程遥控机器人

### How to control a robot with a joystick
### 如何使用操纵杆控制机器人

The Raspberry Pi is amazing in the sense that it can be used to create programs for almost any purpose. I 've seen people create media centres, cloud storage devices, weather stations, video game emulators and various other implementations on this little computer.

树莓派几乎可以通过编程来解决任何问题，从这个角度来讲树莓派简直是令人吃惊的存在。我曾见过有人用这种便携小电脑做出多媒体中心、云存储设备、气象站、游戏模拟器以及其他许多有用的工具。

However, I wanted to start off with something that didn't require lots of software maintenance and decided upon creating a remote-controlled robot. The hardware specifics of this robot will vary from user to user, therefore I want to focus on the coding required to get the robot to move.

然而，我决定创造一个可以遥控并且不需要大量软件维护的机器。机器的硬件特性根据不同的用户而改变，因此我不过多的关注硬件而是在控制机器的代码上下功夫。

I use a joystick to control my robot. To control the motors I use a SmartDrive controller. This is a motor driver that allows you to control up to two high current motors with the Raspberry Pi.

我用一个手柄来控制我的机器。为了控制电机，我使用了SmartDrive。这是一个可以让用户通过树莓派控制两个大电流电机的驱动。

When starting this program, it is important to import the following modules:

程序的开始，需要输入如下的程序段：

The pygame module is used to create a joystick object, the sys module is to be able to quit the program when prompted and the os module is to read the string environment.

Pygame用来创立一个手柄事件。Sys用来停止运行中的程序。Os用来读取字符环境。

This is the code to create the joystick object:

下面是创建手柄事件的代码

A try-except block is recommended because it is important to be able to catch the exception of a pygame. error for debugging purposes.

[pic]

建议使用Try-block代码段，因为调试的时候能发现pygame.error的例外很重要。

When creating the code to actually move the robot, it is helpful to create a separate function for that purpose.

使用分离的函数来使机器运动是十分有效的。

The function is as follows:

函数如下：

When the direction is 0, the motor will run backwards and when the direction is 1 , the motor will run forwards. The SmartDrive speed ranges from 0-1 00 therefore it is important to keep within this scale. This function can now be called whenever prompted.

当direction等于0的时候，马达会向后转。当direction等于1的时候，马达会向前转。要注意smartdrive的速度值区间是0-100，所以编程时要注意这个范围。现在这个函数现在可以在任何时候被调用。

When starting on the main loop of the program, please note that scaling for the joystick axis is required. The get_axis function from pygame ranges from -1 to 1 , with 0 being centered. Therefore we need to scale by 1 00 to be able to use the axis values for the speed parameter in the above move function. The main loop code is as follows:

在写程序的主循环部分要注意需要对手柄轴坐标进行缩放。Pygame的get_axis函数的范围是从-1到1。0的时候是中间。因此我们需要将上面的值放大100倍来使之前函数的Speed参数可以和轴坐标值对应上。代码如下：

The get_button function is used to quit the program and stop the robot from running.

Get_button函数用来停止程序并使机器停止运行。

I have listed all of the electrical parts, motors and other hardware that I have used for this project. I would also recommend checking out your local scrapyard for any motors that you would like to use instead of buying them. My recommendation would be to look for window motors, or electric toy car motors. I decided to use the SmartDrive because it is capable of supporting up to 300W per motor, though I only used motors that ran at 22W each! There is definitely more headroom to use the SmartDrive for more serious projects.

[pic]

我已经列出了我在这个项目中所使用的所有的电子器件、马达以及其他一些硬件。其实我挺推荐你去废品堆放场淘一点用得到的马达，这样你就可以省下一小笔钱了。你可以找一找电动窗马达或者玩具车上的马达。我之所以用SMARTDRIVE是因为它可以为每个马达提供300W的功率，尽管我实际使用时只用了22W。

As mentioned previously, the SmartDrive allows the Raspberry Pi to control up to two high current motors. The SmartDrive is controlled by the Raspberry Pi using the I2C interface.

正如我之前提到的，SMARTDRIVE可以使树莓派最多控制2个大电流电机。它由树莓派上的I2C接口控制。

The programming interface (API ) is coded in Python and contains various different functions that allow you to control the motors in a variety of different ways. Two motors can be connected to the SmartDrive the two black screw terminals labeled M1 and M2. (The third black screw terminal is for power.) I t is also possible to program the SmartDrive with the C language.

程序接口是用PYTHON编写的并且包含了许多可以用不同方法控制马达的函数。马达可以连接到SMARTDRIVE-被标为M1和M2的两个（第三个是用来接电源的）黑色螺丝接线端子上。
当然使用C语言来编写SMARTDRIVE也是可以的。

There are functions that allow you to run the motor in terms of degrees turned, time run in seconds and even for a certain number of rotations. I t also supports rotary encoders. A nice bonus feature of the SmartDrive is that it is capable of providing a 5V output which can be used to power the Raspberry Pi without using another power source.

还有一些函数可以使你设定转身程度、运行时间、甚至某一旋转角度来让马达运行。它还提供旋转的编码器。SMARTDRIVE还有一个很好的特性就是它提供了一个可以驱动树莓派的5V电源，这样我们就不用再找其他的电源了。

Parts List:
元件清单：

1 . SmartDrive:
http://www.openelectrons.com/pages/34

2. Tempest TR1 .3-1 2 Battery (1 2V):
http://www.tempestbatteries.com/html/tr1.3-12.html

3. DreamGrear Shadow USB wireless joystick:
http://www.dreamgear.net/shadow-6-wirelesscontroller-for-ps3-1.html

4. 2x Pittman GM9234E765-R1 motors:
http://www.gearseds.com/competition_motor.html
