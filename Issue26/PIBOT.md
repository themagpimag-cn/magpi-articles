## PIBOT
## PI 机器人

### Part 2: Add the power of speech, hearing and vision to your robot
### 第2部分： 给你的机器人增加语音，听觉，和视觉功能

Introduction
简介

Part 1 of this article in Issue 25 provided an introduction to robotics and gave practical tips for how you can build a fun little robot with your Raspberry Pi. In this second part we will cover some more advanced explorations into Raspberry Pi robotics and demonstrate how the Raspberry Pi can be used to create some impressive robotic behaviours and systems.

本文在上一期的第一部分已经提供了这个机器人的基本介绍，并且给出了关于用你的树莓派做一个有趣的小型机器人的比较实用的 几条小建议。那么第二部分呢，我们将会涉及一些更高级的探索，并且演示怎样用树莓派模拟人类一些令人印象深刻的行为和设计系统。

Three areas will be introduced that each have immense value for useful robotics. These are text to speech, voice recognition and computer vision. Each of these relate to an aspect of human centric abilities - speech, hearing and vision. We saw in Part 1 how robotics is about making computing real world and also that useful robots can sense, process and then act in the world intelligently. In each of our chosen areas we will introduce the technology and give a simple example of how it can be used to do something interesting in a robotic application.

我们将会介绍三个领域，这三个领域对于这个有用处的机器人有巨大价值。这些分别是语音播报，语音识别，和机器视觉。这三个部分每一个都与人类的中枢神经能的一部分有关-听，说，看。上期我们见识了机器人是怎样计算模拟计算真实世界，那个有用的机器人可以感知，处理，然后智能的在这个世界上活动。我们所选的每个领域，都会介绍这项领域的相关技术并且给一个简单的小例子看它是怎样在机器人应用方面做些有趣的事情的。

The first two areas, text-to-speech and voice recognition, are both to do with sound. With a low cost microphone, a speaker and a Raspberry Pi, a world of possibilities opens up and this has been a reason why I ’ve included them in my PiBot project that I have been developing.

前两个领域，语音播报和语音识别都与声音有关。用一个廉价的麦克风，一个扬声器，和一个树莓派，一个具有无限可能的世界打开了，这就是为什么我在我做的这个项目中加入它们。

A speaker gives the robot the power to talk, make interesting sounds and play music. Adding a microphone adds the ability of voice recognition as well as sensing the robot's acoustic environment.

First let's cover making a Raspberry Pi robot talk using text-to-speech.

首先让我们来看看怎样用语音播报功能让树莓派说话。

Power of Speech

演说功能

The best text-to-speech (or TTS) solution I have found for the Raspberry Pi is eSpeak. It has a good range of voices and is not too resource intensive (meaning it leaves processing power for other things too! ). As well as being lightweight, eSpeak provides a simple and straight-forward command line interface that can be easily integrated into Python, as well as other languages. I t even allows us to record straight to a WAV sound file with a simple option in the command line. Best of all, it has a Stephen Hawking-esque sound that gives it a fitting dose of panache. It is also good fun finding out what it mispronounces!

我发现的对于树莓派最好的人工语音播报方案是espeak。它有很好的声音频域而且不是太耗费资源（意味着他会为其他事情省下处理能力）。不仅体积小，espeak还提供了一个简单直白并且很容易被集成到python等其他语言的的命令行接口。他甚至允许我们用一点简单的命令把它直接记录到WAV格式的文件中。最棒的是，他有一个史蒂芬霍金那样的发声器，来给它带来几分派头。发现它是如何发错音也是很有趣的啊！

To get started, the best thing to do is to just try installing eSpeak and see if it works "out of the box". If you are not using HDMI audio, do not forget to have an amplified speaker or headphones plugged in to your Raspberry Pi. For help in setting up audio, or for debugging any audio problems you have, please see this great post on Raspberry Pi Spy (http://www.raspberrypi-spy.co.uk/2013/06/raspberry-pi-command-line-audio/).

首先,我们最好要先试装一下espeak,看看他是否能够"开箱即用",如果你不用HDMI自带的音频,那不要忘了弄一个扬声器或麦克风插到你的树莓派上.如果在安装调试过程中需要帮助,请访问这个在树莓派spy中的公告。

To install eSpeak, on the command line enter:

要安装espeak ，在以下命令行中键入：

This will install the espeak and espeak-data packages. Try issuing a command straight to eSpeak:

这将会安装好espeak这个软件和相关的数据包。尝试着直接发送这条命令给espeak：

The first time eSpeak runs it will probably have a short delay before speaking, which seems to disappear on subsequent executions. You will also probably get quite a long list of warnings about "ALSA lib", "server sockets" and the "jack server". These are harmless and can be ignored. The important thing is that it speaks to you!

espeak 第一次运行的时候 在说话前可能会有一点小的延时，这在接下来的几次运行中这种情况基本就消失了。你还很有可能得到一长串的关于“ALSA lib”“server sockets”“jack server”的警告。不过这些都不会有什么不良影响，你可以将他们忽略。最重要的是它能和你对话了！

More details of TTS and working with eSpeak can be found at http://espeak.sourceforge.net.

更多关于TTS和espeak的细节可以再//espeak.sourceforge.net上找到.

Now that we can give a Raspberry Pi robot the power of speech, what do you think it could be used for? Maybe it could let you know whenever you have new email and read it out aloud. I’m sure you can thinking of several other things.

既然我们能给树莓派机器人发音的能力,你认为它能来做些什么?或许它能让你知道你什么时候来新邮件,并帮你大声朗读出来.我认为你一定能想出不少其他的用处.

As a simple code example let's consider our PiBot’s speech being triggered every time it bumps into something. Here we have added a hardware switch that gets triggered everytime it bumps into anything. From our PiBot Python library we have exposed this event as a function called PiBot.isBumped.

以下是一段简单的代码示例,让我们想想它每次碰到语句时语音功能是怎样被触发的.这里我们给它加了一个硬件开关,每次遇到事件都会被触发.从我们的python库中,我们已经把这种事件封装成一个函数叫PiBot.isBumped.

Power of Hearing
语音识别

One very promising project I have discovered for robotics is called Jasper. This project claims that you can control anything with your voice and their website goes on to explain that, "Jasper is an open source platform for developing always-on, voice controlled applications".

在机器人学中,我发现的一个非常有前景的项目叫Jasper.这个项目宣称你可以用你的声音控制任何事情而且他们的网站进一步解释说,"Jasper 是一个为发展长期语音控制应用的开源平台".

For years ‘voice control’ has been an aspirational technology for the world’s most advanced (and expensive) robots and it is remarkable that this free software now makes this achievable with an inexpensive Raspberry Pi robot.

几年来,语音控制已经成为应用于世界上最先进(且昂贵)的机器人的一项令人振奋的技术,并且值得一提的是这个自由软件已经在廉价的树莓派机器人上成为可能.

Jasper works by identifying specific spoken words (trigger words) that then can activate an action (e.g. execute a Python function). The spoken words that you want to use as triggers are given to Jasper through a string list. Each Python script that you want to use with Jasper needs to contain a string list called WORDS, an isValid() function and a handle() function. The isValid() function relates to words being recognised and the handle() function relates to actions that occur.

Jasper 是通过识别特定的口语单词然后触发事件来工作的(例如 执行一个python 函数).这些你想用来触发事件的口语单词可以通过一个字符串输给Jasper.每一个你要用的python脚本都包含一个叫WORDS的字符串,一个isvalid()函数,和一个handle()函数.isvalid函数与要识别的单词有关,handle函数与要发生的动作有关.

The WORDS string array holds the words that you want to extract from the speech. As an example, let's choose the single word “dance”. We will declare it like this:

WORDS字符数组包含你想从语音中抽取的单词.比如,我们来选一个单词"跳舞",我们可以这样声明:

We will also want to set the priority this script has over other scripts. The higher the number, the more important and further in front of other scripts with similar words it will be. We will set ours at 10 for now. If there is another script with priority less than 10, and it has “dance” in its WORDS array, then our script will be used because it has a higher priority.

我们也想设置这段脚本的优先级高于其他脚本. 数字越高就越重要,在遇到其他同样的单词时就越有可能被执行.我们暂时饿把我们这个单词设置为10;如果另外一段脚本中有一个优先级小于10的,它也包含dance在它的WORDS数组中,那我们的脚本将会被执行,因为它有一个更高的优先级.

The isValid() function checks the transcripted text input from Jasper's audio recognition engine, to determine if this is the correct script. This will check the input from the user and return true if this script is related to the input text.

inValid()函数从Jasper的声音识别引擎中检查输入的文本,并检索出是否有对应的文字.他会检查用户的输入,如果输入文本与脚本相关那就返回真.

The handle() function will basically perform an action in relation to the input. Here is where Jasper will respond to the input. You will need to pass text, mic and profi le as variables which give you more options with Jasper. In this example I get Jasper to acknowledge that it is going to dance and then call a function from our PiBot script to get Jasper dancing!

handle()函数主要是执行与输入相关的动作.这就是Jasper将会对输入做出反应的动作.你可能需要传递text,mic,和profile作为形式参量,这样你就能获得更多选择.在这个例子里我要使Jasper报告它将要跳舞,然后从我们的函数中调用一个函数让它跳舞.

Here is the full script:

More details on Jasper can be found at http://jasperproject.github.io.

Power of Vision

视觉能力

The third area of advanced Raspberry Pi robotics is computer vision. With the Raspberry Pi’s HD camera module you now have the power to capture visual data. Recently the excellent open source computer vision library OpenCV was implemeted on the Raspberry Pi. This now gives great processing capabilities for analysing visual data and opens up a world of possibilities and useful applications. Face recognition, blob tracking, motion detection and gesture mapping are all possible using OpenCV on the Raspberry Pi. I t is of course very exciting to implement these things on a robot. First of all though we will need to install OpenCV on our Raspberry Pi.

高级树莓派机器人的第三个领域就是机器视觉.用树莓派的高清摄像头模组,你就拥有了捕捉视觉数据的能力.最近卓越的开原机器视觉库OPENCV在树莓派上实现了.这将会为分析视觉数据提供巨大的处理能力,并且让树莓派做更多有趣的应用提供了无限可能.面部识别,迷踪循迹,运动检测,手势控制都可以在树莓派上用opencv实现.在机器人上实现这些事情也是非常令人激动的.尽管我们当前要做的还是现在我们的树莓派上装上opencv.

We followed a guide from Adafruit to get OpenCV working with our project. You can read it at https://learn.adafruit.com/raspberry-pi-facerecognition- treasure-box. This also contains links to the image capture, training and configuration scripts mentioned below.

我们在Adafruit上找了一份手册来让我们的树莓派能够运行opencv.你可以在http://learn.adafruit.com/raspberry-pi-face-recognition-treasure-box. 找到. 里面也包含关于图像捕捉和下面要提到的训练配置脚本的链接.

In order to be able to recognise a face we need a number of pictures of that person. We can do that with the Python script capturepositives. py. This accesses the Raspberry Pi camera so needs to run as root::

为了能识别一张脸我们需要许多那个人的照片. 我们可以用这个python脚本-capture-positive.py. 这要获得树莓派摄像头的访问权限,所以你要在根用户下运行.

Multiple images of the same face should be taken from different angles. We use these images to train the face recognition model. This will take some minutes to finish. Enter:

同一张脸的多张照片应该在不同角度拍摄. 我们用这些图片来训练图像识别模型.这可能要花费几分钟. 键入：

After this part we will have to adjust the config.py script in order to configure our servo motor’s movement. The various options are detailed in the above link and will vary depending on your application.

下一步我们必须调整config.by这个脚本来配置我们的伺服电机的移动动作.不同的选项在以上的连接中已经详尽描述,并且会根据你的应用做相应的改变.

The final Python script that we need initialises the Raspberry Pi camera and performs the facial recognition. This version of the code is adapted from the box. py script from Tony Dicola’s OpenCV Facial Recognition project on GitHub (https://github.com/tdicola/pi-facerec-box). This script detects a single face and is the code we need to run our Raspberry Pi in face recognition mode.

我们需要的最后一个python脚本初始化树莓派的摄像头,并且执行面部识别.这一版本的代码是改编自托尼狄谷拉在github上的opencv面部识别工程.这个脚本能检测单张脸,这就是我们要在我们的树莓派上要运行的程序.

Robotic Future

机器人的未来

These topics are quite advanced so if you’ve managed to follow this article completely then you are doing very well!

这些话同时如此的高端大气上档次,所以如果你已经设法读完这篇文章你已经做得很好了.

There are lots of resources online if you want to explore any of these topics further. In particular a number of detailed articles are found on the PiBot website at http://www.pibot.org/how-to and we will be adding more as our adventures into Raspberry Pi robotics continue!

网上有很多资源,如果你想跟深入的研究这些话题可以上网查看.特别说明的是由许多文章是可以在pibot 网站http://www.pibot.org/how-to上找到.我们将继续往树莓派机器人学添加更多资源.

We are now working on computer vision, voice recognition and text-to-speech for our PiBot robot and all this code will be open source and shared with the community too. I don’t know about you but we are excited about making use of the incredible software that is now available on the Raspberry Pi for robotics. Thanks to the Raspberry Pi and its community we can now make a robot that is able to hear you, recognise your face and speak to you as well! Exciting times indeed!

我们正致力于研究树莓派的机器视觉,语音识别,和文本播报功能并且所有的代码都是开源的,也已经在社区内共享.虽然我不认识你,但是我们都会为能在树莓派上用上这么不可思议的软件而高兴.多亏树莓派社区的帮忙,我们现在可以做一个可以听见你,识别你的脸,而且可以与你对话的机器人了.实在非常幸福啊!

Thanks to Aldi Rina, Alex Gray and Steph Tyszka from PiBot for their contributions to this article.

感谢 pibot上Aldi Rina ,Alex Gray 和steph Tyszka三位为此文章的贡献! 

