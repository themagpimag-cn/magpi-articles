## VOICE OVER IP SERVER
## VOIP 服务器

### Using Asterisk to implement a low cost telephone system
### 利用 Asterisk 来实现一个低成本的电话系统

After investigating a number of technology solutions that provide VoIP (Voice-over-Internet Protocol) and IP telephony services, including support for the new trend of UC (Unified Communications) for small businesses, I personally concluded that the Raspberry Pi is able to deliver a totally viable and very low cost solution. When compared to the $100's needed to invest in a dedicated server for a VoIP/UC solution, the cost of a Raspberry Pi and accessories is unmatched.

在研究了一些为小企业提供VoIP（Voice over Internet Protocol）和IP电话服务，包括支持新趋势 UC（统一通信）的技术解决方案之后，我个人认为用树莓派提供一个非常低成本的解决方案是完全可行的。相对于100美元的投资和一个专用的 VoIP/UC 服务器解决方案，树莓派和相应配件在成本方面的优势是无法比拟的。

The Raspberry Pi solution is based on Raspbian running the Asterisk VoIP/UC software. This open source solution provides a high degree of configuration and of course can be used for a multitude of solutions and applications in different areas.

树莓派的解决方案是通过在 Raspbian 系统上运行 Asterisk VoIP/UC 软件来实现的。这个开源解决方案提供了高度灵活的配置项，当然也可以用于许多不同的领域和应用。

This article demonstrates that VoIP/UC solutions are not high risk and do not require high implementation costs.

本文说明了 VoIP/UC 的解决方案并不一定是高风险的，在实施的时候也不一定是需要很高投入的。

Introduction

简介

Telephony has evolved rapidly over the past few decades, migrating from analogue communications to digital communications and IP telephony based on VoIP. This also enables Unified Communications - the integration of real-time communication services such as instant messaging (chat), telephony, data sharing, video conferencing, speech recognition, etc. with non-real-time communication services such as voicemail, email, SMS and fax. UC is not necessarily a single product, but a set of products that provides a consistent, unified, user-interface and userexperience across multiple devices and media-types (http://en.wikipedia.org/wiki/Unified_communications)

在过去的几十年中，电话技术发展迅速，从模拟通信迁移到了基于VoIP的数字通信和IP电话。这也让统一通信成为了可能，统一通信是对实时通信服务，例如即时消息（聊天），电话，数据共享，视频会议，语音识别等和非实时通信服务，例如语音信箱，电子邮件、短信和传真等的集成。统一通信并不是指某一个单一的产品，而是一系列提供了一致的，统一的，跨多个设备和媒体类型的用户界面和用户体验的产品。(http://en.wikipedia.org/wiki/Unified_communications)

VoIP is the transmission of voice over the internet using protocols such as SIP (Session Initiation Protocol) and RTP (Real-time Transport Protocol), among others.

VoIP 是利用某个网络协议，比如SIP协议 (Session Initiation Protocol) 和 RTP协议 (Real-time Transport Protocol) 等，从而实现通过因特网来传输声音。

Baseline

基础

To implement a VoIP/UC solution, the system must meet various industry standards plus the network equipment must be able to differentiate and prioritise voice and video applications over other types of data usage.

要实现一个 VoIP/UC 解决方案，系统必须满足各种行业标准，而且网络设备也必须能够区分出对语音视频数据和其他类型数据的使用。

Basic Components

基本组件

The hardware and software requirements are simple. You probably just need to download the software.

本方案对硬件和软件的要求很简单。你需要做的可能只是下载软件而已。

Hardware:

硬件：

* Raspberry Pi Model B/B+
* 4 GB SD card (minimum)
* 1 A power supply
* Network cable
* Optional SIP phone or SIP adapter (this article uses the Dlink DPH-150SE)

[pic]

* 树莓派B或者B+
* 4 GB SD卡 （最低配置）
* 1A 电源
* 网线
* 可选的 SIP 电话或者 SIP适配器（本文使用 Dlink DPH-150SE）

Software:

软件：

* Raspbian
* Asterisk communications software
* LinPhone soft phone (supports iOS, Android, Blackberry, Linux, Windows and OSX). You can download this from http://www.linphone.org.

* Raspbian
* Asterisk 通信软件
* LinPhone 虚拟电话软件 （支持 iOS, Android, Blackberry, Linux, Windows and OSX)。你可以通过下面链接下载。 http://www.linphone.org

Installation

安装

For the initial setup you may need to use a USB keyboard and mouse with the Raspberry Pi, plus a connection to a monitor. Once configured, the Raspberry Pi will run "headless".

初始安装设置的时候，你可能需要使用一个USB键盘和鼠标连接到 Raspberry Pi 上，再连上一个显示器。配置成功以后，树莓派就可以不需要这些而自己运行了。

The best and easiest way to get the Asterisk software is to download the latest SD card image at http://www.raspberry-asterisk.org/downloads. This contains Raspbian with the Asterisk communication software and FreePBX GUI pre-installed. The image is written to the SD card following the steps at http://www.raspberrypi.org/documentation/installation /installing-images/.

获取 Asterisk 软件最好的和最容易的方法是从这个网站 （http://www.raspberry-asterisk.org/downloads）下载最新的 SD 卡映像文件，它是一个预装了 Asterisk 通信软件和 FreePBX 图形用户界面的 Raspbian 系统。该映像文件是通过在这个网页上（http://www.raspberrypi.org/documentation/installation/installing-images/）的步骤被写到SD卡上的。

When the system starts, login as root with the password raspberry. I f you wish, you can do this remotely. On Windows install the PuTTY SSH client and connect using root@raspbx. On an Apple Mac, simply open the Terminal and enter ssh root@raspbx.local. Later you will want to disable root login via SSH as this is a security weakness. Once logged in, the first command you want to run is:

当系统启动后，用 root 身份和 raspberry 密码登陆。如果愿意，你也可以远程登陆树莓派系统。在 Windows 上安装 PuTTY SSH 客户端并用 root@raspbx 连接树莓派。如果是苹果的 Mac，只需简单的打开终端，输入命令 SSH root@raspbx.local 。你可能以后会想禁止通过 SSH 登陆 root 用户，因为这有可能造成一个安全漏洞。当你登录系统以后，你需要运行的第一个命令是：

This will update all the software to the latest version, including Raspbian and the kernel.
这个命令将更新所有的软件到最新版本，包括 Raspbian 和 Linux 内核。

The next thing you need to do is set up a static IP address. You need to specify the static IP address you want to use, the network mask and the gateway of your router or cable modem. The,

接下来你需要做的是配置静态IP地址。你需要在你的路由器或者猫上指定你想使用的静态IP地址，网络掩码和网关。命令：

command will provide your current IP address and the network mask. Your new static IP will have the same first three octets as your current IP. The last octet must be outside the range that your router uses for dynamic IP addresses. To find the gateway address, enter:

将提供你当前的IP地址，网络掩码。你的新的静态IP地址的前三个字节应该跟你当前的IP相同，最后一个字节必须在你的路由器当前已使用的动态IP地址范围之外。如果想查找网关地址，请输入：

Edit the interfaces file with the command:

通过下面的命令编辑 interface 文件：

Your interfaces file will look something like the screenshot below.

编辑好的 interface 文件应该看起来跟下面截图中的一样。

Note that you need to replace the word dhcp on the eth0 line with the word static. Also be sure to press the <Tab> key once to get the desired indendation.

注意你需要将 eth0 那一行上的 "dhcp" 替换为 "static", 并确保你使用的是 <Tab> 键来达到需要的缩进。

Once saved, reboot to use your new network settings. From now on you can use either the static IP or the raspbx hostname. For example, when using PuTTY to connect with the static IP address above, I can now use root@172.31.15.11.

保存这个文件以后，重启树莓派让新的网络设置生效。现在开始，你就可以使用新的静态IP或者 raspbx 主机名了。例如我现在就可以使用 PuTTY 通过静态IP来连接树莓派： root@172.31.15.11 。

Asterisk configuration

Asterisk的配置

We are now going to use the FreePBX graphical user interface to configure the Asterisk software. This helps to make the process simple and easy. The FreePBX software came pre-installed with the Asterisk image.

我们现在要通过 FreePBX 的图形用户界面来配置 Asterisk 软件。这样可以让整个配置过程变得简单和容易。 FreePBX 是已经在我们下载的那个映像文件里预装好了的软件。

An example architecture diagram is shown below.

如下所示的是一个示例架构图：

To start FreePBX open a web browser and enter http://raspbx or your static IP. (For Apple Mac you will enter http://raspbx.local). This will open the FreePBX Administration page.

要运行 FreePBX， 请打开浏览器并在地址栏输入 http://raspbx 或者树莓派的静态 IP 地址。（对于苹果的 Mac，你需要输入 http://raspbx.local）。这样就打开了 FreePBX 的管理界面。

There are three options:
1 ) FreePBX Administration is used to configure Asterisk
2) User Control Panel is for users to adjust their personal settings
3) Get Support opens the FreePBX website.

这里有三个选项： 
1. FreePBX Administration 用于配置 Asterisk 
2. User Control Panel 供用户调整他们的个人设置 
3. Get Support 将打开 FreePBX 的官方网站

Click on FreePBX Administration. The default login is admin, with the password admin. The Applications menu has various options including Extensions, Conferences and Ring Groups. Click on Extensions.

点击 FreePBX Administration, 默认的登录名是 admin，登陆密码也是 admin。这个软件的菜单有多种选项，包括分机（Extensions），会议（Conferences）和响铃组（Ring Groups）等。请点击分机（Extensions）。

As no extensions exist, you will add a new extension. For the Device option choose Generic SIP Device then click on Submit to go to the next page. There are many options but we will just set the User Extension to 300, the Display Name to Walberto and the secret option to ext300. Click on Submit to add the extension.

由于当前没有分机存在，所以你将添加一个新的分机。Device 选项请选择 Generic SIP Device，然后点击提交（Submit）进入下一个页面。这个页面也有很多的选项，但我们只需要设置用户分机号码为 300，显示名称为 Walberto 和密码为 ext300。单击 Submit 添加该扩展。

On the right side of the screen, click on 300 to view the extension you just added. Verify the port option is set to 5060. Click on Submit, then click on the red Apply Config button to save your changes.

在屏幕的右边，点击 300 来查看你刚刚添加的分机。验证端口（port）选项被设置为 5060。点击 Submit 提交，然后点击那个红色的 Apply Config 按钮来保存所做的更改。

Repeat this procedure for the other extensions that you want to create. I created extensions 301 and 302.

重复这个过程添加其它你需要的分机号，在这里我添加了 301 和 302 分机。

We now configure the IP phone extensions. This will vary by device but we will use the Dlink DPH-150SE as an example. The important settings are to disable the DHCP option, verify the SIP Phone Port Number is 5060, the Registrar Server is the IP address of your Raspberry Pi and in the Others section we enable the Register with Proxy option.

现在，我们需要配置 IP 电话。这个过程根据你的电话设备的型号而不同，在这里我们将使用 Dlink DPH-150SE 作为一个示例。最重要的设置是禁用 DHCP 选项，确认 SIP 电话端口号为 5060，还有注册的服务器是你的树莓派的 IP 地址。在后面的章节中，我们将通过 Proxy 选项来启用服务器注册。

For the SIP Account Settings option we enter the details we previously used when adding extensions using FreePBX. The Authentication User Name is the extension number and the Authentication Password is the secret entry (i.e. ext300).

对于 SIP Account 设置选项，我们需要输入之前通过 FreePBX 添加分机时使用的数据。Authentication User Name 就是之前添加的分机号码，而 Authentication Password 就是我们之前设定的那个密码（即ext300）。对于 SIP Account 设置选项，我们需要输入之前通过 FreePBX 添加分机时使用的数据。Authentication User Name 就是之前添加的分机号码，而 Authentication Password 就是我们之前设定的那个密码（即ext300）。

Softphone configuration

虚拟电话配置

Start Linphone and from the Options menu choose Preferences. Confirm the Network settings are as shown below.

启动 Linphone 并在 Options 菜单中选择 Preferences。确认网络设置如下图所示。

In the Multimedia settings, verify that Echo cancellation is enabled. In Manage SIP Accounts enter your display name. In my example the soft phone is extension 302 so the username is 302. The resulting SIP address is <sip: 302@172.31.15.7>. Click the Add button to register the account with Asterisk.

在 Multimedia settings 选项中， 确认 Echo cancellation 被选上。在 Manage SIP Accounts 选项中输入你的显示名称。在我的例子中，虚拟电话的分机号为302， 所以用户名也为 302。由此而生成的 SIP 地址为 <sip:302@172.31.15.7>。单击 Add 按钮在 Asterisk 上注册该分机的帐号。

Enter your SIP identity from above and the SIP Proxy address (i.e. the IP address of your Raspberry Pi). See the screenshot at the top of the next column for details.

按照下图所示，输入你的 SIP identity 和 SIP Proxy address（即你的树莓派的 IP地址）。

You will then be asked for a password. For extension 302 I set this to be ext302. Click OK and the registration should be confirmed.

然后你将被要求输入密码。对于302分机，我设定的密码是 ext302。单击确定，注册就完成了。

With FreePBX and Asterisk you can implement various services like conference rooms, IVR (Interactive Voice Response), call groups, plus incoming and outgoing calls via the normal PSTN, SIP trunk lines or the internet.

通过 FreePBX 和 Asterisk 可以实现各种服务，如会议室，IVR（交互式语音应答），呼叫组等，还可以通过普通的PSTN电话，SIP中继线或互联网进行呼入和呼出。

The Future

未来

The development of communications using VoIP and the internet is driving the convergence of Unified Communications systems into a single system and environment. FreePBX and Asterisk is a superb example of how sophisticated communication systems can be implemented for very low cost.

VoIP和互联网通讯的发展正在推动统一通信系统融合成一个整体的系统和环境。 FreePBX 和 Asterisk 是一个非常好的例子，它演示了如何用很低的成本来实现复杂的通讯系统。
