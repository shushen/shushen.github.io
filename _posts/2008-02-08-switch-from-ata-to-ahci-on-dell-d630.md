---
id: 19
title: Switch from ATA to AHCI on Dell D630
date: 2008-02-08T21:26:58+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=19
permalink: /19
categories:
  - Computer
tags:
  - ahci
  - sata
---
The following instruction does allow me to switch from ATA to AHCI properly on my Dell D630 laptop:

From [D630 SATA DRIVE INSTALLATION FIX &#8211; Notebook &#8211; Hard Drive &#8211; Dell Community Forum](http://www.dellcommunity.com/supportforums/board/message?board.id=insp_harddrive&thread.id=61287&c=us&l=en&cs=19&s=dhs):

> Go to the Lenovo website <http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-62909> and download the Intel Matrix driver that they have. Once you have downloaded it navigate to the folder and extract out the contents. Then go into the folder that says &#8220;Prepare&#8217; and click &#8220;install&#8221;. It may seem like nothing has happened but you must restart your machine and then go into the BIOS before it reboots. Change the SATA setting to AHCI and the Flash setting(it will prompt you for which Flash must be enabled), and then let your machine fully reboot. Once logged in your machine will find new hardware. Point it to the folder where you extracted the files and it will install the drivers. 

And after done with this installation, one may go to Intel&#8217;s support site to get the [latest driver for Intel Matrix Storage](http://www.intel.com/support/chipsets/imsm/).

References:
  
[1] [Advanced Host Controller Interface &#8211; Wikipedia](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)
  
[2] [Serial ATA &#8211; Wikipedia](http://en.wikipedia.org/wiki/Serial_ATA)

<!--adsense-->
