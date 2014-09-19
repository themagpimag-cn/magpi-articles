## PIBOT
## PI ������

### Part 2: Add the power of speech, hearing and vision to your robot
### ��2���֣� ����Ļ������������������������Ӿ�����

Introduction
���

Part 1 of this article in Issue 25 provided an introduction to robotics and gave practical tips for how you can build a fun little robot with your Raspberry Pi. In this second part we will cover some more advanced explorations into Raspberry Pi robotics and demonstrate how the Raspberry Pi can be used to create some impressive robotic behaviours and systems.

��������һ�ڵĵ�һ�����Ѿ��ṩ����������˵Ļ������ܣ����Ҹ����˹����������ݮ����һ����Ȥ��С�ͻ����˵ıȽ�ʵ�õ� ����С���顣��ô�ڶ������أ����ǽ����漰һЩ���߼���̽����������ʾ��������ݮ��ģ������һЩ����ӡ����̵���Ϊ�����ϵͳ��

Three areas will be introduced that each have immense value for useful robotics. These are text to speech, voice recognition and computer vision. Each of these relate to an aspect of human centric abilities - speech, hearing and vision. We saw in Part 1 how robotics is about making computing real world and also that useful robots can sense, process and then act in the world intelligently. In each of our chosen areas we will introduce the technology and give a simple example of how it can be used to do something interesting in a robotic application.

���ǽ���������������������������������ô��Ļ������о޴��ֵ����Щ�ֱ�����������������ʶ�𣬺ͻ����Ӿ�������������ÿһ������������������ܵ�һ�����й�-����˵�������������Ǽ�ʶ�˻���������������ģ�������ʵ���磬�Ǹ����õĻ����˿��Ը�֪������Ȼ�����ܵ�����������ϻ��������ѡ��ÿ�����򣬶�����������������ؼ������Ҹ�һ���򵥵�С���ӿ����������ڻ�����Ӧ�÷�����Щ��Ȥ������ġ�

The first two areas, text-to-speech and voice recognition, are both to do with sound. With a low cost microphone, a speaker and a Raspberry Pi, a world of possibilities opens up and this has been a reason why I ��ve included them in my PiBot project that I have been developing.

ǰ����������������������ʶ���������йء���һ�����۵���˷磬һ������������һ����ݮ�ɣ�һ���������޿��ܵ�������ˣ������Ϊʲô���������������Ŀ�м������ǡ�

A speaker gives the robot the power to talk, make interesting sounds and play music. Adding a microphone adds the ability of voice recognition as well as sensing the robot's acoustic environment.

First let's cover making a Raspberry Pi robot talk using text-to-speech.

��������������������������������������ݮ��˵����

Power of Speech

��˵����

The best text-to-speech (or TTS) solution I have found for the Raspberry Pi is eSpeak. It has a good range of voices and is not too resource intensive (meaning it leaves processing power for other things too! ). As well as being lightweight, eSpeak provides a simple and straight-forward command line interface that can be easily integrated into Python, as well as other languages. I t even allows us to record straight to a WAV sound file with a simple option in the command line. Best of all, it has a Stephen Hawking-esque sound that gives it a fitting dose of panache. It is also good fun finding out what it mispronounces!

�ҷ��ֵĶ�����ݮ����õ��˹���������������espeak�����кܺõ�����Ƶ����Ҳ���̫�ķ���Դ����ζ������Ϊ��������ʡ�´������������������С��espeak���ṩ��һ����ֱ�ײ��Һ����ױ����ɵ�python���������Եĵ������нӿڡ�����������������һ��򵥵��������ֱ�Ӽ�¼��WAV��ʽ���ļ��С�������ǣ�����һ��ʷ�ٷһ��������ķ�����������������������ͷ������������η�����Ҳ�Ǻ���Ȥ�İ���

To get started, the best thing to do is to just try installing eSpeak and see if it works "out of the box". If you are not using HDMI audio, do not forget to have an amplified speaker or headphones plugged in to your Raspberry Pi. For help in setting up audio, or for debugging any audio problems you have, please see this great post on Raspberry Pi Spy (http://www.raspberrypi-spy.co.uk/2013/06/raspberry-pi-command-line-audio/).

����,�������Ҫ����װһ��espeak,�������Ƿ��ܹ�"���伴��",����㲻��HDMI�Դ�����Ƶ,�ǲ�Ҫ����Ūһ������������˷�嵽�����ݮ����.����ڰ�װ���Թ�������Ҫ����,������������ݮ��spy�еĹ��档

To install eSpeak, on the command line enter:

Ҫ��װespeak ���������������м��룺

This will install the espeak and espeak-data packages. Try issuing a command straight to eSpeak:

�⽫�ᰲװ��espeak����������ص����ݰ���������ֱ�ӷ������������espeak��

The first time eSpeak runs it will probably have a short delay before speaking, which seems to disappear on subsequent executions. You will also probably get quite a long list of warnings about "ALSA lib", "server sockets" and the "jack server". These are harmless and can be ignored. The important thing is that it speaks to you!

espeak ��һ�����е�ʱ�� ��˵��ǰ���ܻ���һ��С����ʱ�����ڽ������ļ������������������������ʧ�ˡ��㻹���п��ܵõ�һ�����Ĺ��ڡ�ALSA lib����server sockets����jack server���ľ��档������Щ��������ʲô����Ӱ�죬����Խ����Ǻ��ԡ�����Ҫ�������ܺ���Ի��ˣ�

More details of TTS and working with eSpeak can be found at http://espeak.sourceforge.net.

�������TTS��espeak��ϸ�ڿ�����//espeak.sourceforge.net���ҵ�.

Now that we can give a Raspberry Pi robot the power of speech, what do you think it could be used for? Maybe it could let you know whenever you have new email and read it out aloud. I��m sure you can thinking of several other things.

��Ȼ�����ܸ���ݮ�ɻ����˷���������,����Ϊ��������Щʲô?������������֪����ʲôʱ�������ʼ�,����������ʶ�����.����Ϊ��һ������������������ô�.

As a simple code example let's consider our PiBot��s speech being triggered every time it bumps into something. Here we have added a hardware switch that gets triggered everytime it bumps into anything. From our PiBot Python library we have exposed this event as a function called PiBot.isBumped.

������һ�μ򵥵Ĵ���ʾ��,������������ÿ���������ʱ����������������������.�������Ǹ�������һ��Ӳ������,ÿ�������¼����ᱻ����.�����ǵ�python����,�����Ѿ��������¼���װ��һ��������PiBot.isBumped.

Power of Hearing
����ʶ��

One very promising project I have discovered for robotics is called Jasper. This project claims that you can control anything with your voice and their website goes on to explain that, "Jasper is an open source platform for developing always-on, voice controlled applications".

�ڻ�����ѧ��,�ҷ��ֵ�һ���ǳ���ǰ������Ŀ��Jasper.�����Ŀ�����������������������κ�����������ǵ���վ��һ������˵,"Jasper ��һ��Ϊ��չ������������Ӧ�õĿ�Դƽ̨".

For years ��voice control�� has been an aspirational technology for the world��s most advanced (and expensive) robots and it is remarkable that this free software now makes this achievable with an inexpensive Raspberry Pi robot.

������,���������Ѿ���ΪӦ�������������Ƚ�(�Ұ���)�Ļ����˵�һ��������ܵļ���,����ֵ��һ����������������Ѿ������۵���ݮ�ɻ������ϳ�Ϊ����.

Jasper works by identifying specific spoken words (trigger words) that then can activate an action (e.g. execute a Python function). The spoken words that you want to use as triggers are given to Jasper through a string list. Each Python script that you want to use with Jasper needs to contain a string list called WORDS, an isValid() function and a handle() function. The isValid() function relates to words being recognised and the handle() function relates to actions that occur.

Jasper ��ͨ��ʶ���ض��Ŀ��ﵥ��Ȼ�󴥷��¼���������(���� ִ��һ��python ����).��Щ�������������¼��Ŀ��ﵥ�ʿ���ͨ��һ���ַ������Jasper.ÿһ����Ҫ�õ�python�ű�������һ����WORDS���ַ���,һ��isvalid()����,��һ��handle()����.isvalid������Ҫʶ��ĵ����й�,handle������Ҫ�����Ķ����й�.

The WORDS string array holds the words that you want to extract from the speech. As an example, let's choose the single word ��dance��. We will declare it like this:

WORDS�ַ������������������г�ȡ�ĵ���.����,������ѡһ������"����",���ǿ�����������:

We will also want to set the priority this script has over other scripts. The higher the number, the more important and further in front of other scripts with similar words it will be. We will set ours at 10 for now. If there is another script with priority less than 10, and it has ��dance�� in its WORDS array, then our script will be used because it has a higher priority.

����Ҳ��������νű������ȼ����������ű�. ����Խ�߾�Խ��Ҫ,����������ͬ���ĵ���ʱ��Խ�п��ܱ�ִ��.������ʱ�������������������Ϊ10;�������һ�νű�����һ�����ȼ�С��10��,��Ҳ����dance������WORDS������,�����ǵĽű����ᱻִ��,��Ϊ����һ�����ߵ����ȼ�.

The isValid() function checks the transcripted text input from Jasper's audio recognition engine, to determine if this is the correct script. This will check the input from the user and return true if this script is related to the input text.

inValid()������Jasper������ʶ�������м��������ı�,���������Ƿ��ж�Ӧ������.�������û�������,��������ı���ű�����Ǿͷ�����.

The handle() function will basically perform an action in relation to the input. Here is where Jasper will respond to the input. You will need to pass text, mic and profi le as variables which give you more options with Jasper. In this example I get Jasper to acknowledge that it is going to dance and then call a function from our PiBot script to get Jasper dancing!

handle()������Ҫ��ִ����������صĶ���.�����Jasper���������������Ӧ�Ķ���.�������Ҫ����text,mic,��profile��Ϊ��ʽ����,��������ܻ�ø���ѡ��.�������������ҪʹJasper��������Ҫ����,Ȼ������ǵĺ����е���һ��������������.

Here is the full script:

More details on Jasper can be found at http://jasperproject.github.io.

Power of Vision

�Ӿ�����

The third area of advanced Raspberry Pi robotics is computer vision. With the Raspberry Pi��s HD camera module you now have the power to capture visual data. Recently the excellent open source computer vision library OpenCV was implemeted on the Raspberry Pi. This now gives great processing capabilities for analysing visual data and opens up a world of possibilities and useful applications. Face recognition, blob tracking, motion detection and gesture mapping are all possible using OpenCV on the Raspberry Pi. I t is of course very exciting to implement these things on a robot. First of all though we will need to install OpenCV on our Raspberry Pi.

�߼���ݮ�ɻ����˵ĵ�����������ǻ����Ӿ�.����ݮ�ɵĸ�������ͷģ��,���ӵ���˲�׽�Ӿ����ݵ�����.���׿Խ�Ŀ�ԭ�����Ӿ���OPENCV����ݮ����ʵ����.�⽫��Ϊ�����Ӿ������ṩ�޴�Ĵ�������,��������ݮ����������Ȥ��Ӧ���ṩ�����޿���.�沿ʶ��,����ѭ��,�˶����,���ƿ��ƶ���������ݮ������opencvʵ��.�ڻ�������ʵ����Щ����Ҳ�Ƿǳ����˼�����.�������ǵ�ǰҪ���Ļ����������ǵ���ݮ����װ��opencv.

We followed a guide from Adafruit to get OpenCV working with our project. You can read it at https://learn.adafruit.com/raspberry-pi-facerecognition- treasure-box. This also contains links to the image capture, training and configuration scripts mentioned below.

������Adafruit������һ���ֲ��������ǵ���ݮ���ܹ�����opencv.�������http://learn.adafruit.com/raspberry-pi-face-recognition-treasure-box. �ҵ�. ����Ҳ��������ͼ��׽������Ҫ�ᵽ��ѵ�����ýű�������.

In order to be able to recognise a face we need a number of pictures of that person. We can do that with the Python script capturepositives. py. This accesses the Raspberry Pi camera so needs to run as root::

Ϊ����ʶ��һ����������Ҫ����Ǹ��˵���Ƭ. ���ǿ��������python�ű�-capture-positive.py. ��Ҫ�����ݮ������ͷ�ķ���Ȩ��,������Ҫ�ڸ��û�������.

Multiple images of the same face should be taken from different angles. We use these images to train the face recognition model. This will take some minutes to finish. Enter:

ͬһ�����Ķ�����ƬӦ���ڲ�ͬ�Ƕ�����. ��������ЩͼƬ��ѵ��ͼ��ʶ��ģ��.�����Ҫ���Ѽ�����. ���룺

After this part we will have to adjust the config.py script in order to configure our servo motor��s movement. The various options are detailed in the above link and will vary depending on your application.

��һ�����Ǳ������config.by����ű����������ǵ��ŷ�������ƶ�����.��ͬ��ѡ�������ϵ��������Ѿ��꾡����,���һ�������Ӧ������Ӧ�ĸı�.

The final Python script that we need initialises the Raspberry Pi camera and performs the facial recognition. This version of the code is adapted from the box. py script from Tony Dicola��s OpenCV Facial Recognition project on GitHub (https://github.com/tdicola/pi-facerec-box). This script detects a single face and is the code we need to run our Raspberry Pi in face recognition mode.

������Ҫ�����һ��python�ű���ʼ����ݮ�ɵ�����ͷ,����ִ���沿ʶ��.��һ�汾�Ĵ����Ǹı�������ҹ�����github�ϵ�opencv�沿ʶ�𹤳�.����ű��ܼ�ⵥ����,���������Ҫ�����ǵ���ݮ����Ҫ���еĳ���.

Robotic Future

�����˵�δ��

These topics are quite advanced so if you��ve managed to follow this article completely then you are doing very well!

��Щ��ͬʱ��˵ĸ߶˴����ϵ���,����������Ѿ��跨������ƪ�������Ѿ����úܺ���.

There are lots of resources online if you want to explore any of these topics further. In particular a number of detailed articles are found on the PiBot website at http://www.pibot.org/how-to and we will be adding more as our adventures into Raspberry Pi robotics continue!

�����кܶ���Դ,��������������о���Щ������������鿴.�ر�˵����������������ǿ�����pibot ��վhttp://www.pibot.org/how-to���ҵ�.���ǽ���������ݮ�ɻ�����ѧ��Ӹ�����Դ.

We are now working on computer vision, voice recognition and text-to-speech for our PiBot robot and all this code will be open source and shared with the community too. I don��t know about you but we are excited about making use of the incredible software that is now available on the Raspberry Pi for robotics. Thanks to the Raspberry Pi and its community we can now make a robot that is able to hear you, recognise your face and speak to you as well! Exciting times indeed!

�������������о���ݮ�ɵĻ����Ӿ�,����ʶ��,���ı��������ܲ������еĴ��붼�ǿ�Դ��,Ҳ�Ѿ��������ڹ���.��Ȼ�Ҳ���ʶ��,�������Ƕ���Ϊ������ݮ����������ô����˼������������.�����ݮ�������İ�æ,�������ڿ�����һ������������,ʶ�������,���ҿ�������Ի��Ļ�������.ʵ�ڷǳ��Ҹ���!

Thanks to Aldi Rina, Alex Gray and Steph Tyszka from PiBot for their contributions to this article.

��л pibot��Aldi Rina ,Alex Gray ��steph Tyszka��λΪ�����µĹ���! 

