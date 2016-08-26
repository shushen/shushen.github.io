---
id: 34
title: 'HOWTO: Use ethtool to configure checksum offload for NICs under Linux'
date: 2008-06-03T11:30:10+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=34
permalink: /34
categories:
  - Computer
  - Linux
  - Networking
tags:
  - Linux
  - networks
---
**What is checksum offloading**

From  [http://www.wireshark.org/docs/wsug\_html\_chunked/ChAdvChecksums.html](http://www.wireshark.org/docs/wsug_html_chunked/ChAdvChecksums.html)

> The checksum calculation might be done by the network driver, protocol driver or even in hardware.
> 
> For example: The Ethernet transmitting hardware calculates the Ethernet CRC32 checksum and the receiving hardware validates this checksum. If the received checksum is wrong Wireshark won&#8217;t even see the packet, as the Ethernet hardware internally throws away the packet.
> 
> Higher level checksums are &#8220;traditionally&#8221; calculated by the protocol implementation and the completed packet is then handed over to the hardware.
> 
> Recent network hardware can perform advanced features such as IP checksum calculation, also known as checksum offloading. The network driver won&#8217;t calculate the checksum itself but will simply hand over an empty (zero or garbage filled) checksum field to the hardware.
  
> Checksum offloading often causes confusion as the network packets to be transmitted are handed over to Wireshark before the checksums are actually calculated. Wireshark gets these &#8220;empty&#8221; checksums and displays them as invalid, even though the packets will contain valid checksums when they leave the network hardware later.
> 
> Checksum offloading can be confusing and having a lot of [invalid] messages on the screen can be quite annoying. As mentioned above, invalid checksums may lead to unreassembled packets, making the analysis of the packet data much harder.
> 
> You can do two things to avoid this checksum offloading problem:
      
> * Turn off the checksum offloading in the network driver, if this option is available.
      
> * Turn off checksum validation of the specific protocol in the Wireshark preferences. 

**How to turn off checksum offload?**
  
Under linux, check the status of offload parameters for the interface (eth0):
  
`ethtool -k eth0`
  
Then turn off tx-checksumming by:
  
`ethtool -K eth0 tx off`
  
Refer to man page of ethtool for more.
