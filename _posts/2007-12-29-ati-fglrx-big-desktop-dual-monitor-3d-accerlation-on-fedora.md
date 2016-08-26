---
id: 12
title: ATI fglrx + Big Desktop + Dual monitor + 3D accerlation on Fedora
date: 2007-12-29T12:06:09+00:00
author: Shu
excerpt: ... the following instructions made the Big Desktop mode on two monitor (and with different resolutions) work, and even comes with 3D acceleration
layout: post
guid: https://www.wavether.com/wp/?p=12
permalink: /12
head_meta:
  - "name='description' content='The following instructions made the Big Desktop mode on two monitor (and with different resolutions) work, and even comes with 3D acceleration'"
categories:
  - Computer
  - Linux
tags:
  - amd
  - ati
  - fedora core
  - Linux
  - xorg
---
Since Fedora Core 6 was released, the ATI fglrx driver from
[rpm.livna.org](http://rpm.livna.org/) has been non-functional.

After struggled with googling and browsing many forums and followed huge number
crappy instructions, finally the following instructions made the Big Desktop
mode on two monitor (and with different resolutions) work, and even comes with
3D acceleration (this is the point of using fglrx, isn't it?):

* [How to build the rpms from ATI drivers (other than using the crappy one from livna.org) for FC6 (now works for v8.29.6)](http://www.phoronix.com/redblog/?p=blog&i=NTU1MA)

* [How to configure Big Desktop](http://www.phoronix.com/redblog/?p=blog&i=MjU1MA)

* [How to enable different resolutions and with 3D!](http://www.ubuntuforums.org/showthread.php?t=301941&page=4)

The essence of the last link (enable different resolutions and with 3D) is as
follows:

    Section "Device"
    Identifier "aticonfig-Device[0]"
    Driver "fglrx"
    Option "VideoOverlay" "on"
    Option "OpenGLOverlay" "off"
    Option "DesktopSetup" "horizontal" #Enable Big Desktop
    Option "Mode2" "1280x1024" #Resolution for second monitor
    Option "EnablePrivateBackZ" "yes" #Enable 3d support < = May Not Work
    Option "HSync2" "65" #This sets the horizontal sync for the secondary display.
    Option "VRefresh2" "60" #This sets the refresh rate of the secondary display.
    BusID "PCI:1:0:0"
    EndSection

Good luck with your fighting with fglrx. I will explore the newer driver when I
have time.

