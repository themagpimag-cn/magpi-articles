PACKET SNIFFING
Raspberry Spy Part 2: network IP addressing 

Educational guide to Wi-Fi networks

Raspberry Spy Part 2: Understanding Wi-Fi

In the first part of this article we concentrated on turning your Raspberry Pi into an effective wireless sniffing tool by swapping the Ethernet port for a Wi-Fi dongle. Here we concentrate on understanding the basic structure of networks and then introduce a powerful set of network analyses facilities.

Networking

The Internet is often pictured as a group of multiply connected nodes all transferring small packets of information which may be instantly rerouted in the event of one or more of the nodes becoming congested or failing completely. In practice electronic failure is rare. The failure considered in the network design of the internet includes having any connection or node being blow to smithereens. After all, the Internet was initially a military communications system - they have a propensity to break things, or know folk who do!

This image of the Internet is a little like looking at the motorway system. Large, wide, fast, high capacity roads with few junctions (nodes) many kilometres apart. A motorway may pass metres from your house but you have no direct access to it. You may live in a cul-de-sac connected to a road, that leads to a B road connected to an A road that eventually connects to the motorway.

In this way you can see how the topology of the Internet is not the multiply connected nodes but looks more like a branch of a Christmas tree. Either way the critical component of any connection is location. Your location may be given by your 'address'. Once a recognised address is given the only other task needed to make a connection is to plan a 'route'. To make our investigations more incisive we need to understand how the Internet deals with addressing and routing problems.

IP Addresses

Real Internet addresses (known as IPv4 addresses) consist of 32 binary bits, for example: 01 1 00000001 01 01 00000000000000001 This provides up to 4.3 billion addresses. This may sound large but the Internet began to run out of addresses long ago!

To make addresses easier to read, humans break the 32 bits into four 8-bit chunks - known as 'bytes' and then convert them to decimal values separated by dots thus:-

01100000 00101010 00000000 00000001
192.168.0.1 dotted decimal notation

Subnetting

An Internet Service Provider (ISP) may have been allocated a block of addresses in the range from 180.181.1.0 to 180.181.7.255.

The ISP has several large customers. Each needs (say) up to 250 addresses for their networks. To organise the addresses effectively and efficiently the ISP could allocate addresses thus:-

180.181.1.0 to 180.181.1.255 to site A
180.181.2.0 to 180.181.2.255 to site B
180.181.3.0 to 180.181.3.255 to site C
180.181.4.0 to 180.181.4.255 to site D

This division of addressing is called 'sub-netting'. (Remember Internet means interconnection of networks). For administration purposes let's refer to each network by it's base address - a network number.

One of the powerful aspects of the Internet is that it devolves sub-netting and we will see a practical example of this that effects you later in the article.

Subnet Mask

A clever and convenient form that is used to describe a complete range of addresses is the 'subnet mask'. The subnet mask is also a 32-bit binary number but if you consider examples you will discover that they have a pattern that look like a bar chart with 1 's emerging from left side of the bit pattern e.g.

11111111111111111111111100000000
11111111111111111111111111111000
11111111111111111111111100000000
11111111111111110000000000000000
11111100000000000000000000000000

The zeros on the right hand side of the mask indicate which bits of an address may be changed. Note for later that the mask can also be described by the length of the 1 's in the chain 255.255.255.0 is /24 in CIDR.

Take the second example above where only the lower three bits of an address may be changed and combine the network 192.168.0.0. A bitwise AND provides the network number:

01100000001010100000000000000000
11111111111111111111111111111000

Perform a bitwise OR with the twos compliment of the mask (a simple and fast digital calculation)

01100000001010100000000000000000
00000000000000000000000000000111

This reveals the highest address in the range i.e. 192.168.0.7. This is also known as the 'broadcast address' and every node on the subnetwork listens to this address.

Applying all of this to our ISP set-up above. The ISP has a network number of 180.181.0.0 and subnet mask 255.255.248.0 The ISP then devolves the four network numbers to site A, B C and D with subnet masks 255.255.255.0

Gateway

One address in the remaining network range has to be the 'gateway'. This is where ALL data, not destined for the local network, is sent. I t's the exit from the cul-de-sac metaphor used above. The local network treats the rest of the world as just one address.

DNS

The references here to binary values show how low level our reference to the Internet is. I f we need to access http://www.bbc.co.uk our network has to resolve this named reference to an IP address. This is achieved by DNS, the Domain Name System. Our local network could keep a complete directory of all name/IP references, which would be a massive undertaking or we could defer to a special DNS service. Entering the IP addresses of these services in the file /etc/resolv.cof file simply resolves this problem. This is the list of servers that will be called upon to convert names to IP addresses.

This completes the minimum requirement for any Internet connected network but remember above where it was stated that the Internet has amost run out of addresses. This happened some time before the explosion in home networking. The solution to providing every house with its own Internet connected network is NAT 'Network Address Translation'.

NAT

Most home users will be connected to the Internet via some kind of modem. This provides Ethernet and/or Wi-Fi in the local area. From the Internet side it has been provided with a single IP network address (referred to as the WAN 'Wide Area Network Address'). NAT translates this address and maps it to a special private range of addresses allowing many devices to be connected inside the home. I t is typical to use a mask of 255.255.255.0 providing 255 local addresses. Local users are deceived into believing they have a full IP but this deceit is provided by the modem.

To make connections even easier NAT is often used in conjunction with DHCP. This is the Dynamic Host Control Protocol. DHCP is used when the Raspberry Pi is first switched on.

Raspberry Pis are manufactured by the bucket load but every Raspberry Pi is not exactly the same. Each has been individually programmed with its own 'MAC address'. At switch on this address is used to call out on any connected network to appeal for local configuration details. DHCP, built into the modem/router responds to the appeal by providing the Raspberry Pi with an individual IP address, details of the local subnet mask, the address of the local gateway and finally the address of any DNS server. With all of these values in place the Raspberry Pi can join the global Internet community!

DHCP will loan each Raspberry Pi an IP address that is re-leased periodically as Internet activity continues. The router will maintain the IP address for the Raspberry Pi even after a period when the Raspberry Pi has been switched off. Should a device be switched off for too long the address can be given to another device. I f instead the Raspberry Pi is permanently configured with an IP address this is called 'static' addressing (as opposed to 'dynamic').

Network Settings

We accessed and modified the key file in the raspberry Pi during the first part of this article. The contents should now make more sense.

By default the DHCP - dynamic setting will look something like this:-

To force a static IP address into your Pi enter:-

Basic Command Line Utilities

These commands may be entered directly from the command line:-

Network Monitoring Applications

With our network knowledge in place we can start to explore using simple tools.

Network Scanning

We need to install some further applications.

Nmap may be used to carefully scan individual IP addresses or complete ranges of addresses. However, large scans can be very time consuming.

Perform a quick test first using:

to report on addresses 1 to 1 6 to check things are working (substitute your own local adress). Alternatively:

where /24 is the CIDR mentioned nomenclature mentioned above.

More complete scans with reporting may be achieved with:

Network Sniffing

Having identified the nodes, we can now look at the data going to and coming from them. This is called 'sniffing'. First obtain the application:

Once downloaded set both ec_uid and ec_gid from 65534 to 0 in /etc/etter.conf. Next:

This command causes ettercap to log any packets on port 53 of any address. (Replace eth0 with wlan0 to tap the WiFi port).

Ports are used to distinguish between network services. Common ports include:-

Your screen could be flooded with details of naming activity on your network or empty. I f nothing is seen try pinging an unknown name on a remote machine to confirm the sniffer is working. Press H for a menu or Q to quit the application. Now try:

to log all http traffic (port 80) on the first 1 6 addresses.

Conclusion

We have covered a good deal of ground in these two articles achieving a least a working system with example commands that may be used as solid introduction to further investigation. For further aid visit the following:

Nmap Security Scanner:
http://nmap.org

Wireshark, a network procol analyser:
http://www.wireshark.org

Pr0mpt, a training program that introduces Open Source and programming:
http://pr0mpt.me

The Ettercap Project:
http://ettercap.github.io/ettercap

Description of IPv4 addressing:
http://en.wikipedia.org/wiki/IPv4

IPv4 address exhaustion:
http://en.wikipedia.org/wiki/IPv4_address_exhaustion