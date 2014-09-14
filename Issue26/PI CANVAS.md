PI CANVAS DIGITAL ART DISPLAY
PI画布的数字艺术显示
How to display dynamic art using a Raspberry Pi
怎样用树莓派来显示动态艺术
In the past digital artists have been limited to static images (prints) when creating wall art. The Pi Canvas allows digital art to be created and displayed on a wall just like a framed print. However, the art is now dynamic which opens up new creative opportunities.
过去数字艺术家创作的墙画仅限于静态的图像。PI画布允许数字艺术家在墙上创作显示就像是在框架中打印的一样。
并且，这种艺术充满活力，开启了新的创新机遇。
In this article I will describe how you can make a Pi Canvas using your Raspberry Pi to produce a display of dynamic art - art which can optionally interact with viewers.
在本文中我将阐述怎样用你的树莓派制作一个PI画布来显示动态艺术，一项能够与观众交互的艺术。
What is Pi Canvas?
什么是PI画布
Pi Canvas is a Raspberry Pi mounted on an HDTV that has a USB connector to power the Raspberry Pi. The Pi Canvas has no keyboard, no mouse, nor does it respond to the TV remote control. I t is simple to use. Just hang it on the wall, plug it in, press the power button and let it do its thing.
PI画布是一个连接在高清电视上的、通过USB接口给它供电树莓派。PI画布没有键盘，鼠标，也不依赖电视遥控器。它使用很简单：就把它挂在墙上，接上电源，打开开关，然后让它工作即可。
The Pi Canvas can operate 24/7 or be powered on and off as required. I t can also be made to interact with its environment through electronic sensors (e.g. ultrasonic or infrared) which opens up even more creative opportunities.
PI画布可以7*24小时不间断工作，或者根据需要打开或关闭电源。它也可以通过传感器（比如超声波，红外线等）感知周围的环境来使它更富有创造性。
How to make a Pi Canvas?
怎样做一个PI画布
The hardware and software used are all popular, open source and well documented. Basic knowledge of the hardware and software is not covered here as there are many excellent tutorials available online. The Pi Canvas was developed in the Faulhaber Fab Lab at the Suncoast Science Center in Sarasota, Florida. I t supports STEAM education (Science + Technology + Engineering + Art + Mathematics) for all ages. For more details, please visit http://www.suncoastscience.org.
使用的硬件和软件都是流行的，并且开源的，编写好的文档。基本的硬件和软件知识不包含在这篇文章中，网上有很多很好的教程。
PI画布在弗罗里达州萨拉索塔（美国西部城市）Suncoast科学中心的Faulhaber Fab实验室中开发出来的。该机构支持所有年龄的STEAM教育（自然科学，科技，工程学，艺术，数学），了解更多细节，请浏览：http://www.suncoastscience.org
Pi Canvas hardware
PI画布的硬件
The Pi Canvas hardware requirements are simple:
Raspberry Pi (model A or B)
USB <-> micro USB cable (for power)
HDMI male to male coupler
HDTV (e.g. VIZIO model E390-A1 )
PI画布所需的硬件很简单：
树莓派（A版或B版）
USB连接线（供电）
HDMI公头连接线
高清电视（比如 VIZIO 型号：E390-A1）
While any HDTV can be used, the example HDTV is particularly good as it has a USB connector sufficient for powering the Raspberry Pi. I t also has a recessed area on the back for attaching the Raspberry Pi, which allows for flush wall mounting. Finally it has a narrow, clean bezel which makes a nice frame.
任何高清电视都是可行的，但VIZIO特别好，因为它有一个可以给树莓派充足电流的USB接口。背板上有一个可以放置树莓派的凹槽，使得可以安装到平面墙上。最后，它有一个很窄的，清洁的边框使得画面更加美观。
Pi Canvas software
PI画布的软件
Just like the hardware, the Pi Canvas software requirements are simple and familiar to many:
像PI画布的硬件一样，软件也很简单熟悉：
Latest Raspbian OS
Chromium web browser
HTML5 Canvas element
JavaScript
最新的Raspbian操作系统
谷歌浏览器
HTML5 Canvas标签
JavaScript脚本
Chromium has a kiosk mode for full screen operation with no browser decoration or controls. The HTML5 Canvas element offers good graphics capabilities for art and is fast. Finally JavaScript is an easy but capable language for browsers. This software combination runs very well on a Raspberry Pi.
Chrom浏览器有一个kiosk模块来支持全屏操作而不需要浏览器的控制。HTML5 Cancas标签为画图提供了一个又好又快的图像
处理模块。而JavaScript是一个简单的并且功能强大的脚本语言。这些软件都能在树莓派上运行良好。
Example JavaScript tutorials can be found at http://www.w3schools.com/js/. You should also visit http://www.html5canvastutorials.com.
关于简单地JavaScript教程可以参考：http://www.w3schools.com/js/，你也可以浏览：http://www.html5canvastutorials.com。
Pi Canvas configuration
PI画布的配置
In addition to the normal Raspberry Pi setup, the following steps are required to make a Pi Canvas with the listed hardware and software. You will need separate power for the Raspberry Pi because the HDTV does not supply adequate power for this step.
除了树莓派常规的设置外，以下硬件和软件的设置步骤对于制作一个PI画布是必需的。你需要单独给树莓派供电，因为高清电视机不能提供足够的电流来使其运行。
Enter the following on the command line:
在命令行中输入
When the Raspberry Pi Software Configuration Tool appears, enable the option to boot to desktop.
当树莓派的配置工具出现时，选择进入桌面选项。
Next we will install the chromium package plus some other utilities. The unclutter package removes the mouse cursor from the screen after some inactivity.
接下来我们将安装谷歌浏览器和其他的一些实用工具包。光标闪烁一会后，整理好的包将被安装。
Your dynamic artwork is a web page. On the next page there is some example artwork code. Enter this code into a text editor and save it as sample. html. Put this sample file into the /home/pi/ folder.
你的动态艺术品是一个网页，下一页有一个网页示例代码。将这些代码输入到一个文本文档保存为sample.html。
然后把这个简单文档放到 /home/pi/floder目录下。
When the Raspberry Pi is powered on, we want to automatically start Chromium with the artwork running. On the command line enter:
当打开树莓派时，我们想在谷歌浏览器上自动运行艺术品。在命令行下输入：
Comment out the following lines by prefixing them with a #:
把下列行添加注释#
Then add the following lines:
然后添加一下行：
In nano you should see the following:
在nano编辑器下将会是一下样子：
To save your changes press <Ctrl>+X, then Y then <Enter>.
然后按<Ctrl>+x保存更改，Y确认，然后按<Enter>
When you restart your Raspberry Pi, the sample artwork should automatically appear. To open a second login press <Ctrl>+<Alt>+F2. To return back to the art display press <Ctrl>+<Alt>+F7.
当你重启你的树莓派时，这个简单地艺术品就自动启动了。按住<Ctrl>+<Alt>+F2打开第二个命令行登陆页面，按住<Ctrl>+<Alt>+F7返回显示界面。
Pi Canvas artwork
PI画布艺术品
The Suncoast Science Center has a display area for showcasing inventions of all kinds created in the Fab Lab. Here is a screen shot of a Pi Canvas on display in the Fab Lab display area. The artwork is titled "Loose Weave Digital Fabric". In April it won an award at the Art Center Sarasota ¡°One World¡± exhibition.
Suncoast科学中心展览了各种各样在Fab实验室创造的展示发明。一下是一个PI画布显示在Fab实验的屏幕截图。这件艺术品称为“松散的数字织物”在四月份 萨拉索塔（美国西部城市）的“同一个世界”艺术展中获得了一项大奖。
The artwork creates a new digital fabric every ten minutes. Drawing the digital fabric is an important visual aspect of the artwork and takes about five minutes.
这个艺术品每隔十分钟将创建一副新的数字织物。画一副数字织物对这件艺术品来说是很重要的视觉，它大概需要五分钟。
The fabric colour is random and the thread colours are random within +/- 45 degrees of the fabric colour on the HSLA (Hue - Saturation - Lightness - Alpha) colour wheel.
这幅织物的颜色是随机的，线条的颜色跟织物的颜色成+/-45`在HSLA(色调，饱和度，亮度，透明度)色环上。
Pi Canvas sample artwork code
PI画布简单地艺术品代码
Here is a sample artwork file which draws a "starburst" approximately every 1 0 seconds. The hues remain within 30 degrees of the initial, random hue on the HSLA colour wheel.
这里展示的是一个简单艺术品代码，它大约每隔十秒钟画一副光芒。最初的色调有三十个等级，是随机变换的。
What happens if you change the values of dhue or tension?
如果你改变dhue或者tension的值会发生什么情况呢？
