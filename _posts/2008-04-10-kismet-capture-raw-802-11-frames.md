---
id: 24
title: How to capture raw 802.11 frames with Kismet
date: 2008-04-10T12:25:42+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=24
permalink: /24
categories:
  - Computer
  - Linux
  - Networking
tags:
  - 802.11
  - fedora core
  - Linux
  - networks
  - wifi
  - wireless
---
## Introduction

Kismet is an 802.11 layer2 wireless network detector, sniffer, and intrusion
detection system. Kismet will work with any wireless card which supports raw
monitoring (rfmon) mode, and can sniff 802.11b, 802.11a, 802.11n, and 802.11g
traffic (devices and drivers permitting).

Kismet identifies networks by passively collecting packets and detecting
standard named networks, detecting (and given time, decloaking) hidden
networks, and inferring the presence of non-beaconing networks via data
traffic.

## System requirements

Kismet is licensed under GPL. Most popular Linux distributions come with Kismet
packages that can be installed from online repositories. A Win32 port is also
available but only works with certain commercial wireless drivers that enables
capture under Windows - almost none of the Windows drivers comes with your
wireless card supports raw capture.

Check if your wireless card is supported against the list in Section 12,
Capture Sources, of [Kismet
README](http://www.kismetwireless.net/documentation.shtml#readme)

## Installation

This HOWTO assumes you are running Fedora Core 8 and have installed a supported
driver for your wireless card.

1. Login as _root_

2. Install _kismet_ packages

        # yum -y install kismet kismet-extra

3. Modify `kismet.conf` to tell `kismet` about the capture source

        # vi /etc/kismet/kismet.conf

   Search for `source=` and specify the source type, interface, and give a name
to the capture source. For example, if you have an Intel PRO/Wireless 2200BG
card installed as eth1 and are using ipw2200 driver, specify the following:

        source=ipw2200,eth1,ipw2200

4. Now you are ready to run `kismet` as root

        # kismet

    You will be shown the panel of kismet and it's started capturing the raw 802.11
frames and stores the packets in a variety of formats under `/var/log/kismet`

5. Optionally you can install and use wireshark to parse the \*.dump' file and
view the frames in very details. Below is a screenshot of Wireshark showing a
capture by Kismet.

![A capture of Kismet being displayed in
WireShark](/assets/2008/04/wireshark-kismet.png)


## References

* [Official site of Kismet](http://www.kismetwireless.net)
* [Kismet README](http://www.kismetwireless.net/documentation.shtml#readme)

