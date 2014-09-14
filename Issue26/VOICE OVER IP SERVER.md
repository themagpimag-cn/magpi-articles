VOICE OVER IP SERVER
Using Asterisk to implement a low cost telephone system

After investigating a number of technology solutions that provide VoIP (Voice-over-Internet Protocol) and IP telephony services, including support for the new trend of UC (Unified Communications) for small businesses, I personally concluded that the Raspberry Pi is able to deliver a totally viable and very low cost solution. When compared to the $100's needed to invest in a dedicated server for a VoIP/UC solution, the cost of a Raspberry Pi and accessories is unmatched.

The Raspberry Pi solution is based on Raspbian running the Asterisk VoIP/UC software. This open source solution provides a high degree of configuration and of course can be used for a multitude of solutions and applications in different areas.

This article demonstrates that VoIP/UC solutions are not high risk and do not require high implementation costs.

Introduction

Telephony has evolved rapidly over the past few decades, migrating from analogue communications to digital communications and IP telephony based on VoIP. This also enables Unified Communications - the integration of real-time communication services such as instant messaging (chat), telephony, data sharing, video conferencing, speech recognition, etc. with non-real-time communication services such as voicemail, email, SMS and fax. UC is not necessarily a single product, but a set of products that provides a consistent, unified, user-interface and userexperience across multiple devices and media-types (http://en.wikipedia.org/wiki/Unified_communications)

VoIP is the transmission of voice over the internet using protocols such as SIP (Session Initiation Protocol) and RTP (Real-time Transport Protocol), among others.

Baseline

To implement a VoIP/UC solution, the system must meet various industry standards plus the network equipment must be able to differentiate and prioritise voice and video applications over other types of data usage.

Basic Components

The hardware and software requirements are simple. You probably just need to download the software.

Hardware:

? Raspberry Pi Model B/B+
? 4 GB SD card (minimum)
? 1 A power supply
? Network cable
? Optional SIP phone or SIP adapter (this article uses the Dlink DPH-150SE)

Software:

? Raspbian
? Asterisk communications software
? LinPhone soft phone (supports iOS, Android, Blackberry, Linux, Windows and OSX). You can download this from http://www.linphone.org.

Installation

For the initial setup you may need to use a USB keyboard and mouse with the Raspberry Pi, plus a connection to a monitor. Once configured, the Raspberry Pi will run "headless".

The best and easiest way to get the Asterisk software is to download the latest SD card image at http://www.raspberry-asterisk.org/downloads. This contains Raspbian with the Asterisk communication software and FreePBX GUI pre-installed. The image is written to the SD card following the steps at http://www.raspberrypi.org/documentation/installation /installing-images/.

When the system starts, login as root with the password raspberry. I f you wish, you can do this remotely. On Windows install the PuTTY SSH client and connect using root@raspbx. On an Apple Mac, simply open the Terminal and enter ssh root@raspbx.local. Later you will want to disable root login via SSH as this is a security weakness. Once logged in, the first command you want to run is:

This will update all the software to the latest version, including Raspbian and the kernel.

The next thing you need to do is set up a static IP address. You need to specify the static IP address you want to use, the network mask and the gateway of your router or cable modem. The,

command will provide your current IP address and the network mask. Your new static IP will have the same first three octets as your current IP. The last octet must be outside the range that your router uses for dynamic IP addresses. To find the gateway address, enter:

Edit the interfaces file with the command:

Your interfaces file will look something like the screenshot below.

Note that you need to replace the word dhcp on the eth0 line with the word static. Also be sure to press the <Tab> key once to get the desired indendation.

Once saved, reboot to use your new network settings. From now on you can use either the static IP or the raspbx hostname. For example, when using PuTTY to connect with the static IP address above, I can now use root@172.31.15.11.

Asterisk configuration

We are now going to use the FreePBX graphical user interface to configure the Asterisk software. This helps to make the process simple and easy. The FreePBX software came pre-installed with the Asterisk image.

An example architecture diagram is shown below.

To start FreePBX open a web browser and enter http://raspbx or your static IP. (For Apple Mac you will enter http://raspbx.local). This will open the FreePBX Administration page.

There are three options:
1 ) FreePBX Administration is used to configure Asterisk
2) User Control Panel is for users to adjust their personal settings
3) Get Support opens the FreePBX website.

Click on FreePBX Administration. The default login is admin, with the password admin. The Applications menu has various options including Extensions, Conferences and Ring Groups. Click on Extensions.

As no extensions exist, you will add a new extension. For the Device option choose Generic SIP Device then click on Submit to go to the next page. There are many options but we will just set the User Extension to 300, the Display Name to Walberto and the secret option to ext300. Click on Submit to add the extension.

On the right side of the screen, click on 300 to view the extension you just added. Verify the port option is set to 5060. Click on Submit, then click on the red Apply Config button to save your changes.

Repeat this procedure for the other extensions that you want to create. I created extensions 301 and 302.

We now configure the IP phone extensions. This will vary by device but we will use the Dlink DPH-150SE as an example. The important settings are to disable the DHCP option, verify the SIP Phone Port Number is 5060, the Registrar Server is the IP address of your Raspberry Pi and in the Others section we enable the Register with Proxy option.

For the SIP Account Settings option we enter the details we previously used when adding extensions using FreePBX. The Authentication User Name is the extension number and the Authentication Password is the secret entry (i.e. ext300).

Softphone configuration

Start Linphone and from the Options menu choose Preferences. Confirm the Network settings are as shown below.

In the Multimedia settings, verify that Echo cancellation is enabled. In Manage SIP Accounts enter your display name. In my example the soft phone is extension 302 so the username is 302. The resulting SIP address is <sip: 302@172.31.15.7>. Click the Add button to register the account with Asterisk.

Enter your SIP identity from above and the SIP Proxy address (i.e. the IP address of your Raspberry Pi). See the screenshot at the top of the next column for details.

You will then be asked for a password. For extension 302 I set this to be ext302. Click OK and the registration should be confirmed.

With FreePBX and Asterisk you can implement various services like conference rooms, IVR (Interactive Voice Response), call groups, plus incoming and outgoing calls via the normal PSTN, SIP trunk lines or the internet.

The Future

The development of communications using VoIP and the internet is driving the convergence of Unified Communications systems into a single system and environment. FreePBX and Asterisk is a superb example of how sophisticated communication systems can be implemented for very low cost.